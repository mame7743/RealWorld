# Alpine Linuxの基本イメージを使用
FROM elixir:1.14-alpine

EXPOSE 4000

# アプリケーションディレクトリを作成
RUN mkdir /app
WORKDIR /app

# 必要なパッケージをインストール
RUN apk add --no-cache build-base npm inotify-tools git postgresql-client

# Phoenix 1.7をインストール
RUN mix local.hex --force && \
    mix local.rebar --force && \
    mix archive.install hex phx_new 1.7.10 --force

# # phoenixのプロジェクトを作成
# RUN mix phx.new . --app ${app_name} --install && \
#     mix ecto.setup

# 依存関係をインストール
# COPY mix.exs mix.lock ./
# RUN mix do deps.get, deps.compile

# COPY . .

# ENTRYPOINT ["mix", "phx.server"]