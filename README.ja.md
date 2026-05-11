# ocr_mac

> macOS標準のVisionおよびQuartzフレームワークを使用して、画像やPDFファイルからテキストを抽出するコマンドラインOCRツールです。

このリポジトリでは、柔軟なBashスクリプトと、シンプルなコンパイル済みのObjective-Cバイナリの2つの実装を提供しています。

## 機能

-   PDF、JPG、PNGファイルからテキストを抽出します。
-   日本語と英語をサポートしています。
-   外部依存関係はありません。macOSに組み込まれているフレームワーク（`Vision`、`Quartz`）を使用します。
-   PDFラスタライズ時のDPIを調整可能です（シェルスクリプト版のみ）。

## 要件

-   macOS 11.0以降。
-   Xcode Command Line Tools（ネイティブバイナリ版でのみ必要）。

## 実装

### 1. シェルスクリプト (`ocr.sh`)

`osascript`を使用してmacOSの基盤となるフレームワークにアクセスする、自己完結型のBashスクリプトです。コンパイルは不要で、複数ファイルの処理やコマンドラインオプションをサポートしています。

#### **使い方**

まず、スクリプトに実行権限を付与します。
```bash
chmod +x ocr.sh
```

次に、対象のファイルを指定してスクリプトを実行します。抽出されたテキストは標準出力に出力されます。

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

#### **オプション**

```text
Usage: ./ocr.sh [--lang <LANG>] [--dpi <VALUE>] <input1> <input2> ...

Options:
  -h, --help      Show help
  --lang <LANG>   Set OCR language (ja/en) (default: ja)
  --dpi <VALUE>   Set DPI value for PDF rasterization (default: 200)
```

### 2. ネイティブバイナリ (`ocr.m`)

Objective-Cで書かれたコマンドラインツールで、特に大きなドキュメントにおいてより高速なパフォーマンスが期待できます。使用前にコンパイルする必要があります。

#### **コンパイル**

付属のシェルスクリプトを使用してソースコードをコンパイルします。
```bash
sh c-ocr.sh
```
このコマンドは `clang` を使用して、`ocr` という名前の実行可能ファイルを作成します。

#### **使い方**

コンパイルされたバイナリは、引数として単一のPDFファイルのパスを受け付けます。

```bash
./ocr document.pdf
```
*注: このバージョンは設定がハードコードされています。日本語と英語の両方のテキストを認識し、200 DPIに固定されています。*

## 参考元

このプロジェクトは、以下の記事で解説されている手法に基づいています。
-   [macOS のデフォルト状態でコマンドラインからOCR処理を行う - TeX Alchemist Online](https://doratex.hatenablog.jp/entry/20230629/1687977178)

## ライセンス

このプロジェクトはライセンスが設定されておらず、public domainとして公開されています。
