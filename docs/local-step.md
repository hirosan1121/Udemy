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
   cd ../backend
   npm install
   .envファイルを作成する(.env.exampleを参照)
   npm start
   ```
   - .env ファイルの例
     ```
     MONGOURL = mongodb+srv://your_name:your_password@cluster0.cmwizql.mongodb.net/realsns?retryWrites=true&w=majority&appName=Cluster0
     ```
3. アプリケーションの立ち上げ
   ```
   別のbashを開く
   cd ../frontend
   npm start
   ```
