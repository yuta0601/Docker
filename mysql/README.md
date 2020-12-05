# MySQL on Docker

## 起動方法
```
docker run --rm -d -it --name mysql -e MYSQL_ROOT_PASSWORD=root yuta0601/mysql
```

## コンテナに入る
```
docker exec -it mysql bash
```

## myslq起動
```
root@a9a963002e50:/# mysql -u root -p
Enter password: root
```