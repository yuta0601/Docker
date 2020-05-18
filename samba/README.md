# samba on Docker

## Docker Pull
`docker pull yuta0601/samba`

## Preparation

```sh
mkdir /srv/samba
chown 100 /srv/samba
```

## Docker Run
`docker run --restart=always --name samba -p 139:139 -p 445:445 -v /srv/samba:/pub -d yuta0601/samba -s "pub;/pub;yes;no;no;yuta,guest" -u "yuta;0000" -u "guest;0000"`

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
ユーザ１;  
ユーザ2

`-u yuta;0000`  
`-u guest;0000`  
ユーザ名;パスワード

## 状況確認
### コンテナの動作状況確認
`docker ps -a`
### コンテナのログを確認
`docker logs samba`
### コンテナにログイン
`docker exec -it samba /bin/bash`