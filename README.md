# ocr_mac

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

> A command-line OCR tool for macOS that extracts text from images and PDF files using the native Vision and Quartz frameworks.

This repository provides two implementations: a flexible Bash script and a simple, compiled Objective-C binary.

## Features

-   Extracts text from PDF, JPG, and PNG files.
-   Language support for Japanese and English.
-   No external dependencies; uses built-in macOS frameworks (`Vision`, `Quartz`).
-   Adjustable DPI for PDF rasterization (shell script version).

## Requirements

-   macOS 11.0 or later.
-   Xcode Command Line Tools (required only for the native binary version).

## Implementations

### 1. Shell Script (`ocr.sh`)

This is a self-contained Bash script that uses `osascript` to access the underlying macOS frameworks. It requires no compilation and supports multiple files and command-line options.

#### **Usage**

First, make the script executable:
```bash
chmod +x ocr.sh
```

Then, run the script with your files. The extracted text will be printed to standard output.

```bash
# OCR a PDF with default settings (Japanese, 200 DPI)
./ocr.sh document.pdf

# OCR an image, specifying English
./ocr.sh --lang en image.png

# OCR multiple files at once
./ocr.sh file1.jpg file2.pdf

# Show help for all options
./ocr.sh --help
```

#### **Options**

```text
Usage: ./ocr.sh [--lang <LANG>] [--dpi <VALUE>] <input1> <input2> ...

Options:
  -h, --help      Show help
  --lang <LANG>   Set OCR language (ja/en) (default: ja)
  --dpi <VALUE>   Set DPI value for PDF rasterization (default: 200)
```

### 2. Native Binary (`ocr.m`)

This is a command-line tool written in Objective-C for potentially faster performance, especially with large documents. It must be compiled before use.

#### **Compilation**

Use the provided shell script to compile the source code:
```bash
sh c-ocr.sh
```
This command uses `clang` to create an executable file named `ocr`.

#### **Usage**

The compiled binary accepts a single PDF file path as an argument.

```bash
./ocr document.pdf
```
*Note: This version has hardcoded settings. It recognizes both Japanese and English text and uses a fixed DPI of 200.*

## Source / Inspiration

This project is based on the technique described in the following article:
-   [macOS のデフォルト状態でコマンドラインからOCR処理を行う - TeX Alchemist Online](https://doratex.hatenablog.jp/entry/20230629/1687977178)
