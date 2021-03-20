#

### build

```
cd 0.15.0
docker build -t mtool:0.15.0 .
```

### check mtool

```
cd ..
docker run --rm -ti mtool:0.15.0 mtool-client -v
```

### add ca.crt, validator_config.json, staking.json to conf

### mount ca.crt when run mtool-client show version

```
cd ..
docker run --rm -ti -v `pwd`/conf:/root/ca mtool:0.15.0 mtool-client -v
```

### add <node_ip>:domain3 to host

### nginx config(platon.conf) change hostname(domain3) to server(ssl)

```
server {
    listen 443 ssl;                # 监听443端口, 开启ssl(必须)
    server_name domain3;

    ssl_certificate      /etc/nginx/conf.d/server.crt;
    ssl_certificate_key  /etc/nginx/conf.d/server.key;

    location / {
        proxy_pass http://127.0.0.1:6789;                     # platon http rpc 接口地址
        auth_basic "input password";                          # 这里是提示信息
        auth_basic_user_file /etc/nginx/conf.d/platonpasswd;  # 这里填写刚才生成的密码文件路径
    }
}

```

### mount ca.crt when run mtool-client and update_validator

```
docker run --rm -ti -v `pwd`/conf:/root/ca mtool:0.15.0 mtool-client update_validator --details "超元立方社区,提供更多获取ATP/LAT的正确姿势.VX:Kidd1997" --config /root/ca/validator_config.json --keystore /root/ca/staking.json
```
