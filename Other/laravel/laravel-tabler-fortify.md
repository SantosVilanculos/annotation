# Laravel & Tabler & Fortify

```sh
composer install
composer update

composer require livewire/livewire
php artisan livewire:publish --config

composer require intervention/image

composer require propaganistas/laravel-phone

composer require --dev barryvdh/laravel-debugbar

composer require --dev barryvdh/laravel-ide-helper

pnpm install
pnpm update

pnpm install -D sass
pnpm install -D @tabler/core

touch ./database/database.sqlite
php artisan migrate

php artisan ide-helper:generate
php artisan ide-helper:models -N

mkdir -p ./resources/views/pages
```

### /.env & /.env.example

```sh
APP_PREVIOUS_KEYS=
```

### /.gitignore

```sh
/_ide_helper_models.php
/_ide_helper.php
/composer.lock
/pnpm-lock.yaml
```

### /config/livewire.php

```php
<?php

return [
    'inject_assets' => false,
    'pagination_theme' => 'bootstrap'
]
```

### /resources/js/app.js

```js
import "@tabler/core/dist/js/demo-theme";
import "@tabler/core/dist/js/tabler";
import TomSelect from "tom-select";
import "./bootstrap";

window.TomSelect = TomSelect;
```

### /resources/css/app.css

```css
@import "@tabler/core/dist/css/tabler.min.css";
@import "@tabler/core/dist/css/tabler-flags.min.css";
@import "@tabler/core/dist/css/tabler-payments.min.css";
@import "@tabler/core/dist/css/tabler-vendors.min.css";
@import "tom-select/dist/css/tom-select.min.css";
```

### /resources/views/components/layouts/app.blade.php

```php
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>{{ config('app.name') }}</title>

  <link rel="icon" href="{{ asset('favicon.ico') }}" type="image/x-icon">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">

  @livewireStyles
  
  @if (file_exists(public_path('build/manifest.json')) || file_exists(public_path('hot')))
    @vite(['resources/css/app.css', 'resources/js/app.js'])
  @endif


</head>

<body>
  {{ $slot }}

  @livewireScripts
</body>

</html>
```

### /app/Providers/AppServiceProvider.php

```php
<?php

namespace App\Providers;

use Carbon\CarbonImmutable;
use Illuminate\Support\Facades\DB;
use Illuminate\Pagination\Paginator;
use Illuminate\Support\Facades\Date;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Support\ServiceProvider;
use Illuminate\Validation\Rules\Password;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     */
    public function register(): void
    {
        //
    }

    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        DB::prohibitDestructiveCommands($this->app->isProduction());

        Model::shouldBeStrict(!$this->app->isProduction());
        Model::unguard();

        Password::defaults(fn() => $this->app->isProduction() ? Password::min(8) : null);

        Date::use(CarbonImmutable::class);

        Paginator::useBootstrapFive();

        RedirectIfAuthenticated::redirectUsing(fn() => '/');
    }
}
```
