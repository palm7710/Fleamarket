# ベースイメージとしてNode.jsのAlpineイメージを使用
FROM node:20-alpine

# 必要なツール（bashとcurl）をインストール
RUN apk add --no-cache bash curl

# Node.jsとnpmを直接インストール
RUN apk add --no-cache nodejs npm

# 作業ディレクトリを設定
WORKDIR /app

# プロジェクトファイルをコピー
COPY . /app

# 依存関係をインストール
RUN npm install

# 開発サーバーを起動
CMD ["npm", "start"]
