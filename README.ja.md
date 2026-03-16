# ocr_mac

English README is here: [README.md](README.md)

この文書の英語版はこちらです: [README.md](README.md)

MacのためのOCRツール。

## 機能
- PDFドキュメントや画像ファイルの光学文字認識(OCR)を行う
- 日本語と英語をサポートしています
- PDFラスター化のカスタムDPI値を設定できます

## 要件
- macOS 10.15 (Catalina) 以降

## 使い方
1. リポジトリをクローンします:
   ```
   git clone https://github.com/your-username/ocr_mac.git
   ```
2. プロジェクトディレクトリに移動します:
   ```
   cd ocr_mac
   ```
3. OCRスクリプトをコンパイルします:
   ```
   bash c-ocr.sh
   ```
4. OCRツールを実行します:
   ```
   ./ocr [--lang <LANG>] [--dpi <VALUE>] <input1> <input2> ...
   ```
   - `--lang <LANG>`: OCR言語を設定します (ja/en、デフォルト: ja)
   - `--dpi <VALUE>`: PDF rasteri化のためのDPI値を設定します (デフォルト: 200)
   - `<input1>`, `<input2>`, ...: 処理するPDFまたは画像ファイルのパス

## ライセンス
このプロジェクトは [MIT License](LICENSE) のもとで公開されています。
