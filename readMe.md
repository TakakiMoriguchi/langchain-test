### FastAPI開発入門
Chapter4 Dockerイメージの作成時のテンプレートファイル群
以下、次に実行するFastAPIのインストールなどの手順

※ DEMOAPPはプロジェクト名を指定する事。

1. .dockerenvフォルダの作成
```commandline
mkdir .dockerenv
```

2. Poetry環境のセットアップ
```commandline
docker compose run --entrypoint "poetry init --name DEMOAPP --dependency fastapi --dependency uvicorn[standard]" DEMOAPP
```

3. FastAPIのインストール
```commandline
docker compose run --entrypoint "poetry install --no-root" DEMOAPP
```

4. ビルド
```commandline
docker compose build --no-cache
```

5. サンプルファイルの作成
```commandline
mkdir api && touch api/__init__.py && touch api/main.py
```

6. サンプルファイルの編集
```commandline
# api/main.py
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}
```

7. サーバーの起動
```commandline
docker compose up
```