## Dusk 1.8 güncelleme
```shell
systemctl stop rusk
```

```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.8/itn-installer.sh | sudo sh
```

```shell
service rusk start
```


Loglara bakın
```shell
tail -F /var/log/rusk.log
```

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
