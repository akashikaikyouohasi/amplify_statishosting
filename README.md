## 概要
「静的ウェブサイトをホスティングする」のチュートリアル用のリポジトリ

create-react-appで作成しただけ。

## Amplifyのビルド設定
```
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm install
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: build
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```

### frontend
フロントエンドのビルドコマンド。
バックエンドは**backend**セクションを追加する必要がある。

### phases
**preBuild**、**build**、**postBuild**のタイミングを定義して、各シーケンス中で実行するコマンドを定義する

#### preBuild
ビルドの開始前に実行するコマンド。

今回は依存関係を解決するために依存パッケージのインストール

#### build
ビルドコマンド。

#### postBuild
ビルドコマンド完了後に実行するコマンド
今回は特になり

### artifacts
**base-directory**にビルド対象が存在するディレクトリを指定し、**files**にデプロイするファイルを指定する。

ここで定義したものだけをAmplifyでホスティングする模様

### cache
依存関係をキャッシュして、次のビルド時間を短縮してくれるみたい。

