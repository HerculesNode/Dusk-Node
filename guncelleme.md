## Dusk 1.3 güncelleme
```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.3/itn-installer.sh | sudo sh
```

```shell
service rusk start
```

```shell
tail -F /var/log/rusk.log
```

- Bu şekilde çıktı almanız gerekiyor
![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/ea3a2bca-fab6-454d-be2c-6727cd9b623d)


## Blok kontrol

```shell
curl --location --request POST 'http://127.0.0.1:8080/02/Chain' --header 'Rusk-Version: 0.7.0-rc' --header 'Content-Type: application/json' --data-raw '{
    "topic": "gql",
    "data": "query { block(height: -1) { header { height } } }"
}' | jq '.block.header.height'
```

- bu şekilde çıktı almalısınız

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/e61f7029-5a34-4325-ab6e-62b194a7b832)


## Stake kontrol

```shell
rusk-wallet stake-info
```

- bu şekilde çıktı almalısınız

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/8af2bb2d-375d-423b-90f7-fde29157b0e2)
