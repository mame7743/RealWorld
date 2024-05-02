# RealWorld

[Elixir実践入門](https://amzn.asia/d/71koeDq)の第11章の写経。

[Devcontainer](https://code.visualstudio.com/docs/remote/remote-overview)を使って開発できるようにしてみた。

## 必要なもの

- [Docker Desktop](https://docs.docker.com/desktop/)
- [vscode](https://code.visualstudio.com/download)
- [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Phoenix プロジェクト作成

```sh
docker-compose run --rm app mix phx.new . --app realworld
```

## データベースの作成

`config/dev.exs` の中身を書き換え、PostgreSQLサーバーとの接続できるようにする。

```diff
    # Configure your database
    config :realworld, Realworld.Repo,
    username: "postgres",
    password: "postgres",
-   hostname: "localhost",
+   hostname: "db"
    database: "realworld_dev",
    stacktrace: true,
    show_sensitive_data_on_connection_error: true,
    pool_size: 10
```

下記コマンドを実行し、データベースを作成。

```sh
docker-compose run --rm app mix ecto.setup
```
