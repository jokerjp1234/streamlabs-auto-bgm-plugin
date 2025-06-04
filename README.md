# StreamLabs Auto BGM Plugin

画面認識による自動BGM再生プラグイン for StreamLabs

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/jokerjp1234/streamlabs-auto-bgm-plugin/releases)
[![StreamLabs](https://img.shields.io/badge/StreamLabs-Compatible-green.svg)](https://streamlabs.com/)

## ✨ 概要

このプラグインは、ゲーム画面やアプリケーション画面を監視し、登録された画像と類似する場面を検出すると自動的にBGMを再生する機能を提供します。画面が変わると音楽は自動で停止し、配信者の手間を大幅に削減できます。

## 🌟 主な機能

### 🖼️ 画面認識機能
- **リアルタイム画面監視**: 設定した間隔で画面をキャプチャして監視
- **高精度画像認識**: 3つの認識方式（ヒストグラム、特徴点、テンプレート）
- **感度調整**: グローバルおよびシーン別の認識感度設定
- **GPU アクセラレーション**: 高速な画像処理（対応環境）

### 🎶 音声制御機能
- **自動BGM再生**: シーン検出時の自動再生
- **フェードイン/フェードアウト**: スムーズな音量変化効果
- **音量・再生速度調整**: リアルタイムでの音声パラメータ制御
- **ループ再生**: 継続的なBGM再生
- **手動停止**: いつでも音楽を手動で停止可能

### 📋 シーン管理機能
- **ドラッグ&ドロップ登録**: 画像とBGMの簡単登録
- **検索・ソート・フィルタリング**: 効率的なシーン管理
- **使用統計の追跡**: シーン別使用回数
- **インポート/エクスポート**: シーンデータのバックアップと共有

## 🚀 インストール方法

### 1. プラグインファイルの配置
```bash
# リポジトリをクローンまたはダウンロード
git clone https://github.com/jokerjp1234/streamlabs-auto-bgm-plugin.git

# StreamLabsプラグインフォルダに配置
# Windows: %APPDATA%/Streamlabs OBS/plugins/
# Mac: ~/Library/Application Support/Streamlabs OBS/plugins/
```

### 2. StreamLabsでの設定
1. StreamLabs OBSを起動
2. `設定` → `プラグイン` → `カスタムプラグイン`
3. プラグインフォルダを指定
4. `Auto BGM Player`を有効化

### 3. 権限の許可
- 画面キャプチャの許可
- 音声再生の許可
- ローカルストレージアクセスの許可

## 📖 使い方

### 基本的な使用手順

#### 1. シーンの登録
1. `登録`タブを開く
2. シーン名を入力
3. 参照画像をアップロード（PNG/JPEG/WebP、最大5MB）
4. BGM音声をアップロード（MP3/WAV/OGG、最大10MB）
5. 認識感度を調整（0.1〜1.0）
6. `シーンを登録`ボタンをクリック

#### 2. 監視の開始
1. `制御`タブを開く
2. `監視開始`ボタンをクリック
3. 画面キャプチャの許可を与える
4. 画面監視が開始される

#### 3. 音声設定の調整
- **音量**: 0〜100%で調整
- **再生速度**: 0.5x〜2.0xで調整
- **フェードイン時間**: 0〜5秒
- **フェードアウト時間**: 0〜5秒

## 🛠️ 技術仕様

### サポートファイル形式
- **画像**: PNG, JPEG, WebP (最大5MB)
- **音声**: MP3, WAV, OGG (最大10MB)

### 画像認識アルゴリズム
1. **ヒストグラム比較**: RGB色分布の比較
2. **特徴点マッチング**: エッジ特徴の抽出と比較
3. **テンプレートマッチング**: ダウンサンプリング後の直接比較

### ブラウザ要件
- Chrome 70+ / Firefox 65+ / Safari 12+
- WebRTC（画面キャプチャ）対応
- Web Audio API対応
- ES6+対応

### 権限要件
- `screen_capture`: 画面キャプチャ
- `audio_playback`: 音声再生
- `storage`: ローカルデータ保存

## 📁 ファイル構成

```
streamlabs-auto-bgm-plugin/
├── manifest.json          # プラグイン設定ファイル
├── main.html             # メインHTML
├── main.js               # メインコントローラー
├── styles.css            # スタイルシート
├── imageProcessing.js    # 画像処理クラス
├── audioManager.js       # 音声管理クラス
├── sceneManager.js       # シーン管理クラス
├── README.md            # ドキュメント
├── LICENSE              # ライセンス
└── docs/                # 詳細ドキュメント
    ├── INSTALLATION.md   # インストールガイド
    ├── API.md           # API仕様
    └── TROUBLESHOOTING.md # トラブルシューティング
```

## 🔧 カスタマイズ

### 新しい認識アルゴリズムの追加
```javascript
// imageProcessing.js に追加
async calculateCustomSimilarity(imageData1, imageData2) {
    // カスタム認識ロジックを実装
    return similarity; // 0-1 の値を返す
}
```

### カスタムフェードエフェクト
```javascript
// audioManager.js に追加
async customFadeEffect(targetVolume, duration, curve) {
    // カスタムフェード曲線を実装
}
```

## 🐛 トラブルシューティング

### よくある問題

#### 画面キャプチャが動作しない
- ブラウザの画面共有許可を確認
- HTTPSでアクセスしているか確認
- 他の画面キャプチャソフトとの競合を確認

#### 音声が再生されない
- ブラウザの音声許可を確認
- 音声ファイル形式を確認
- 音量設定を確認

#### 認識精度が低い
- 認識感度を調整
- 参照画像を高品質なものに変更
- 認識方式を変更

#### メモリ使用量が多い
- キャプチャ解像度を下げる
- チェック間隔を長くする
- 不要なシーンを削除

### ログの確認
プラグイン内のログパネルでリアルタイム動作状況を確認できます。

## 🤝 コントリビューション

### 開発への参加
1. フォークしてください
2. フィーチャーブランチを作成 (`git checkout -b feature/AmazingFeature`)
3. 変更をコミット (`git commit -m 'Add some AmazingFeature'`)
4. ブランチにプッシュ (`git push origin feature/AmazingFeature`)
5. プルリクエストを作成

### バグレポート
GitHub Issuesで報告してください：
- 環境情報（OS、ブラウザ、StreamLabsバージョン）
- 再現手順
- 期待される動作
- 実際の動作
- エラーメッセージ

## 📄 ライセンス

MIT License - 詳細は [LICENSE](LICENSE) ファイルを参照

## 🙏 謝辞

- StreamLabs開発チーム
- Web Audio API contributors
- オープンソースコミュニティ

## 📮 サポート

- **GitHub Issues**: バグレポート・機能要求
- **Discussions**: 使用方法の質問・アイデア共有
- **Wiki**: 詳細ドキュメント・チュートリアル

---

**注意**: このプラグインは非公式のものです。StreamLabsとは関係ありません。

## 🔄 バージョン履歴

### v1.0.0 (2025-06-04)
- 初回リリース
- 基本的な画面認識機能
- 自動BGM再生機能
- シーン管理機能
- 設定UI実装

### 今後の予定
- AI画像認識の統合
- より多くの音声フォーマットサポート
- クラウド同期機能
- マルチモニター対応
- ホットキー対応