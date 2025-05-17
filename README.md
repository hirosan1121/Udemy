# 📘 Real-SNS

ユーザー同士が投稿・いいねを通じて交流できる SNS アプリケーションです。

---

## 📖 概要

- 主な機能のリスト
  1. ユーザー登録
  2. ログイン
  3. ポスト
  4. いいね

---

## 🛠️ 技術スタック

| 分類           | 技術        |
| -------------- | ----------- |
| フロントエンド | React       |
| バックエンド   | Node.js     |
| データベース   | MongoDB     |
| その他         | JS/HTML/CSS |

---

## ⚙️ 環境構築手順

1. リポジトリをクローン

   ```
   bash
   git clone https://github.com/hirosan1121/Udemy

   ```

2. サーバーの立ち上げ
   ```
   cd Udemy
   cd frontend
   npm install
   cd Udemy
   cd backend
   .envファイルを作成する(.env.exampleを参照)
   npm start
   ```
3. アプリケーションの立ち上げ
   ```
   別のbashを開く
   cd ../frontend
   npm start
   ```

## 📁 ディレクトリ構成

  <pre> 
  Udemy/ 
    ├── frontend/          # フロントエンドアプリ
    ├── backend/           # バックエンドAPI
    ├── .env.example       # 環境変数のサンプル
    └── README.md
     </pre>
