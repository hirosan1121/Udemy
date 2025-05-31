# API 設計書（Real SNS）

本プロジェクトの API 設計をまとめます。エンドポイント、リクエスト・レスポンス例、主な仕様を記載しています。

---

## 認証・ユーザー関連

### ユーザー登録

- **POST** `/api/auth/register`
- **Body**
  ```json
  {
    "username": "string",
    "email": "string",
    "password": "string"
  }
  ```
- **Response**
  - 200: 登録ユーザー情報（JSON）
  - 500: エラー

### ログイン

- **POST** `/api/auth/login`
- **Body**
  ```json
  {
    "email": "string",
    "password": "string"
  }
  ```
- **Response**
  - 200: ユーザー情報（JSON）
  - 404: ユーザーが見つからない
  - 400: パスワード不一致
  - 500: エラー

### ユーザー情報取得

- **GET** `/api/users?userId=xxx` または `/api/users?username=xxx`
- **Response**
  - 200: ユーザー情報（パスワード等除外）
  - 500: エラー

### ユーザー情報更新

- **PUT** `/api/users/:id`
- **Body**
  ```json
  {
    "userId": "string", // 自分のID
    ...更新したいフィールド
  }
  ```
- **Response**
  - 200: 更新成功メッセージ
  - 403: 権限エラー
  - 500: エラー

### ユーザー削除

- **DELETE** `/api/users/:id`
- **Body**
  ```json
  {
    "userId": "string" // 自分のID
  }
  ```
- **Response**
  - 200: 削除成功メッセージ
  - 403: 権限エラー
  - 500: エラー

---

## 投稿関連

### 投稿作成

- **POST** `/api/posts`
- **Body**
  ```json
  {
    "userId": "string",
    "desc": "string",
    "img": "string (画像パス)"
  }
  ```
- **Response**
  - 200: 作成された投稿（JSON）
  - 500: エラー

### 投稿編集

- **PUT** `/api/posts/:id`
- **Body**
  ```json
  {
    "userId": "string",
    ...編集したいフィールド
  }
  ```
- **Response**
  - 200: 編集成功メッセージ
  - 403: 権限エラー
  - 500: エラー

### 投稿削除

- **DELETE** `/api/posts/:id`
- **Body**
  ```json
  {
    "userId": "string"
  }
  ```
- **Response**
  - 200: 削除成功メッセージ
  - 403: 権限エラー
  - 500: エラー

### 投稿取得

- **GET** `/api/posts/:id` ...投稿 ID で取得
- **GET** `/api/posts/profile/:username` ...ユーザーの投稿一覧
- **GET** `/api/posts/timeline/:userId` ...タイムライン取得
- **Response**
  - 200: 投稿情報（JSON）
  - 500: エラー

---

## 画像アップロード

### 画像アップロード

- **POST** `/api/upload`
- **FormData**
  - `file`: 画像ファイル
  - `name`: 保存名
- **Response**
  - 200: アップロード成功メッセージ
  - 500: エラー

---

## モデル構造（抜粋）

### User

```js
{
  username: String,
  email: String,
  password: String,
  profilePicture: String,
  coverPicture: String,
  followers: Array,
  followings: Array,
  isAdmin: Boolean,
  desc: String,
  city: String,
  from: String,
  relationship: Number
}
```

### Post

```js
{
  userId: String,
  desc: String,
  img: String,
  likes: Array,
  createdAt, updatedAt
}
```

---

## 備考

- 認証は JWT 等は未実装（サンプル用）
- パスワードは平文保存のため、実運用時はハッシュ化推奨
- 画像は `/public/images/` 配下に保存

---

以上が本プロジェクトの API 設計概要です。
