# testproject

Docker で PostgreSQL 18 と Adminer を起動する開発環境です。

## 必要なもの

- Docker Desktop（WSL の場合は WSL Integration で Ubuntu をオン）

## セットアップ

```bash
git clone <このリポジトリのURL>
cd <リポジトリ名>
cp .env.example .env
```

`.env` の `POSTGRES_PASSWORD` を自分のパスワードに書き換えてから起動してください。

## 起動

```bash
docker compose up -d
```

## 接続

psql で接続：

```bash
docker compose exec db psql -U testproject -d testproject
```

Adminer（ブラウザ）：http://127.0.0.1:8080

- データベース種類：PostgreSQL
- サーバー：db
- ユーザー名・パスワード・データベース：`.env` の値

## 停止

```bash
docker compose down      # 停止（データは残る）
docker compose down -v   # データごと削除
```

※ `.env` の値は初回起動時だけ使われます。あとから変更した場合は `docker compose down -v` してから起動し直してください。