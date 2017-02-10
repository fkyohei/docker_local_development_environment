# Dockerを使用したローカル開発環境

## 環境
・WEBサーバ1台  
・APIサーバ1台  
・DBサーバ1台  
・キャッシュサーバ1台  
・Redisサーバ1台  

## 環境作成
### Docker For Macのインストール
[https://docs.docker.com/docker-for-mac/](https://docs.docker.com/docker-for-mac/)

### gitからファイルをダウンロード
```sh
git clone https://github.com/fkyohei/docker_local_development_environment.git
```

### コンテナをバックグラウンドで起動
```sh
cd docker_local_development_environment
docker-compose up -d
```

### 起動中のコンテナのプロセスを確認
```sh
docker-compose ps
# または
docker ps
```

### コンテナを停止
```sh
docker-compose stop
```

### Dockerfileを編集した場合、再ビルドを実行
```sh
# container_nameを指定しない場合は全コンテナ
docker-compose build [container_name]
```

### コンテナログイン
```sh
docker exec -it [container_name] /bin/bash
```

### オレオレ証明書
```
openssl genrsa 2048 > localhost.key
openssl req -new -key localhost.key > localhost.csr
openssl x509 -req -days 3650 -signkey localhost.key < localhost.csr > localhost.crt
```

### mysqlデータ永続化
busyboxを使用してローカルディレクトリにバインド

## 参考
[http://koni.hateblo.jp/entry/2017/01/28/150522](http://koni.hateblo.jp/entry/2017/01/28/150522)  
[http://qiita.com/jey0taka/items/3fca0d0acb8aa4278284](http://qiita.com/jey0taka/items/3fca0d0acb8aa4278284)
