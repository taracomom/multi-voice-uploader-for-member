# Multi Voice Uploader

音声ファイルの文字起こしと複数プラットフォーム（Stand.fm、Voicy、Spotify）への投稿を管理するElectronアプリケーションです。

## セットアップ

### 必要な環境

- Node.js (v16以上)
- Python 3.7以上
- ffmpeg（Whisperで音声処理に必要）

### インストール手順

1. **Node.jsの依存関係をインストール**
   ```bash
   npm install
   ```

2. **Pythonの依存関係をインストール**
   ```bash
   pip install -r requirements.txt
   ```

   または、Whisperのみインストールする場合：
   ```bash
   pip install openai-whisper
   ```

3. **ffmpegのインストール**

   - macOS: `brew install ffmpeg`
   - Windows: [ffmpeg.org](https://ffmpeg.org/download.html) からダウンロード、または `choco install ffmpeg`
   - Linux: `sudo apt-get install ffmpeg`

## 使い方

### アプリの起動

```bash
npm start
```

### 基本的な操作

1. **音声ファイルの追加**
   - 「ファイルを追加」ボタンをクリック
   - 音声ファイル（.m4a, .mp4, .wav, .mp3）を選択
   - ファイルは自動的に `.m4a` フォルダに保存されます

2. **文字起こしの実行**
   - ファイル一覧から文字起こししたいファイルを選択
   - 「文字起こし」ボタンをクリック
   - 初回実行時はWhisperモデル（デフォルト: base）がダウンロードされます
   - 文字起こし結果は `text` フォルダに保存されます

3. **投稿の管理**
   - 各プラットフォーム（Stand.fm、Voicy、Spotify）への投稿ボタンから投稿を実行
   - 投稿済みのファイルにはステータスが表示されます
   - 投稿状態は `metadata.json` に保存されます

### データの保存場所

- 音声ファイル: `.m4a/`
- 文字起こし結果: `text/`
- Markdownファイル: `md/`
- メタデータ: `metadata.json`

## トラブルシューティング

### 文字起こしが失敗する場合

- Pythonが正しくインストールされ、PATHに登録されているか確認
- `pip install openai-whisper` でWhisperがインストールされているか確認
- ffmpegがインストールされ、PATHに登録されているか確認

### 投稿が失敗する場合

- 各プラットフォームにログインしているか確認
- ブラウザが正常に起動しているか確認

## ビルド

配布用のアプリをビルドする場合：

```bash
npm run build
```

ビルド結果は `dist` フォルダに出力されます。
