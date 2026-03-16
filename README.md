# ocr_mac
日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

OCR tool for Mac.

## Features
- Performs optical character recognition (OCR) on PDF documents and image files
- Supports Japanese and English languages
- Allows setting custom DPI value for PDF rasterization

## Requirements
- macOS 10.15 (Catalina) or later

## Usage
1. Clone the repository:
   ```
   git clone https://github.com/your-username/ocr_mac.git
   ```
2. Navigate to the project directory:
   ```
   cd ocr_mac
   ```
3. Compile the OCR script:
   ```
   bash c-ocr.sh
   ```
4. Run the OCR tool:
   ```
   ./ocr [--lang <LANG>] [--dpi <VALUE>] <input1> <input2> ...
   ```
   - `--lang <LANG>`: Set the OCR language (ja/en, default: ja)
   - `--dpi <VALUE>`: Set the DPI value for PDF rasterization (default: 200)
   - `<input1>`, `<input2>`, ...: Path(s) to the PDF or image file(s) to be processed

## License
This project is licensed under the [MIT License](LICENSE).
