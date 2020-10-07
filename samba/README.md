# samba on Docker
公式のリポジトリがなかったためスター数の多いdperson/sambaを使用
## Preparation

```sh
mkdir ~/samba/pub
chmod 777 ~/samba/pub
```

## Docker Run
docker-comopose コマンドで起動するように修正

### docker-compose
`docker-compose up -d`

### docker run コマンド
`docker run --restart=unless-stopped --name samba -p 139:139 -p 445:445 -v ~/samba/pub:/mnt/pub:rw -d dperson/samba -s "public;/mnt/pub;yes;no;no;yuta,guest" -u "guest1;0000" -u "guest2;0000"`

|オプション|指定内容|
|---|---|
|`--restart=always`|PC起動時にsambaコンテナを自動起動|
|`--name samba`|起動コンテナに名前(samba)を付与|
|`-p 139:139`|ポート転送|
|`-p 445:445`|ポート転送|
|`-v /srv/samba:/pub`|共有ディレクトリのマウント(PCの/srv/sambaをコンテナの/pubにマウント)|
|`-d`|バックグラウンド実行|

`-s "pub;/pub;yes;no;no;yuta,guest"`  
共有ディレクトリの名前;  
共有ディレクトリのパス;  
プラウズの可否;  
リードオンリーの可否;  
ゲスト利用の可否;  
ユーザ１,
ユーザ2

`-u guest1;0000`  
`-u guest2;0000`  
ユーザ名;パスワード

#### 状況確認
- コンテナの動作状況確認  
`docker ps -a`
- コンテナのログを確認  
`docker logs samba`
- コンテナにログイン  
`docker exec -it samba /bin/bash`