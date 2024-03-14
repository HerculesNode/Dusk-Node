## Dusk 1.8 güncelleme
```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.8/itn-installer.sh | sudo sh
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
ruskquery block-height
```

## Stake kontrol

```shell
rusk-wallet stake-info
```

- bu şekilde çıktı almalısınız

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/8af2bb2d-375d-423b-90f7-fde29157b0e2)
