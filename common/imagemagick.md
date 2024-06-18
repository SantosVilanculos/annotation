# Image Magick

## Installation

### GNU Linux

#### Debian

```sh
sudo apt install imagemagick
```

## Usage

### Convert

#### \*.ico with multiple sizes

```sh
convert ./favicon.png -define icon:auto-resize="256,128,96,64,48,32,16" ./favicon.ico
```

### Resize

```sh
convert ./favicon.png -resize x152 ./favicon.png ./apple-touch-icon-152x152.png
```
