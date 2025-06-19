# Snip-n-Clip

A simple bash script that captures a screenshot of a selected area, performs OCR (Optical Character Recognition) on it, and copies the extracted text to the clipboard.

## Features

- **Area Selection**: Use your mouse to select any area of your screen
- **OCR Processing**: Automatically extracts text from the screenshot using Tesseract
- **Clipboard Integration**: Copies the extracted text directly to your clipboard
- **Desktop Notifications**: Shows a notification when text is successfully copied

## Dependencies

Make sure you have the following packages installed:

- `gnome-screenshot` - For taking screenshots
- `tesseract-ocr` - For OCR text extraction
- `wl-clipboard` - For clipboard operations (Wayland)
- `libnotify-bin` - For desktop notifications

### Installation on Ubuntu/Debian:
```bash
sudo apt install gnome-screenshot tesseract-ocr wl-clipboard libnotify-bin
```

### Installation on Fedora:
```bash
sudo dnf install gnome-screenshot tesseract wl-clipboard libnotify
```

### Installation on Arch Linux:
```bash
sudo pacman -S gnome-screenshot tesseract wl-clipboard libnotify
```

## Usage

1. Make the script executable:
   ```bash
   chmod +x snip-n-clip
   ```

2. Run the script:
   ```bash
   ./snip-n-clip
   ```

3. Select the area containing text you want to extract
4. The text will be automatically copied to your clipboard
5. A notification will confirm the operation

### Note:
You might want to add it to PATH for easy access, or assign it to a keyboard shortcut.

## How it Works

1. Creates a temporary image file with timestamp
2. Uses `gnome-screenshot -a` to capture a user-selected area
3. Processes the image with Tesseract OCR for English text
4. Copies the extracted text to clipboard using `wl-copy`
5. Shows a desktop notification upon completion
6. Automatically cleans up by using a temporary file

## Notes

- The script is designed for Wayland environments (uses `wl-copy`)
- For X11 environments, you might need to replace `wl-copy` with `xclip`
- OCR accuracy depends on image quality and text clarity
- Currently configured for English text recognition (`-l eng`)

## Customization

You can modify the script to:
- Change the OCR language by editing the `-l eng` parameter
- Use different screenshot tools
- Adjust notification messages
- Add support for X11 clipboard (`xclip`)