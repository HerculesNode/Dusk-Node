# Dusk Node işlemleri

Dusk teşvikli Node kurulum işlemi. Ödül alabilmeniz için;  
- 26 Şubat itibarıyla düğümlerin çalışır durumda olması gerekiyor. Bu, "sayıldığı" ve çalışma süresinin kaydedileceği zamandır
- 26 Şubat - 15 Mart 2024 arası çalışması gerekiyor.
- Ödüller : <BR>
250K DUSK tüm düğümlere eşit olarak dağıtılacak <BR>
250K DUSK, stake edilen tutara göre POAP airdrop'uyla dağıtılacak


## Linkler
 * [Hercules Telegram](https://t.me/HerculesNode)
 * [Hercules Twitter](https://twitter.com/Herculesnode)

## Sistem özellikleri

| 2-4 Gb Ram  | Ubuntu 22.04 |  50-100 Gb SSD | 
| ----------------- | ----------------- | ----------------- |


## Sistem Güncelleme ve kütüphaneler
```shell
sudo apt update && sudo apt upgrade -y
```

## Rust kurulumu yapın  

Kurulumu yapın

```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.7/itn-installer.sh | sudo sh
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/5ee16ea6-6e42-4bba-b3ed-caeb52759a05)


## Cüzdan oluşturma ve Faucet işlemi 

- Bu adrese gidin ve cüzdan oluşturun Kelimeleri kaydedin. Kelimeleri büyük harf veriyor bunları küçük harf olarak değiştirin 
- https://wallet.dusk.network/setup/

- Cüzdan adresinizi kopyalayın Dusk discord kanalına girin ve `Dusk Testnet Faucet` botuna mesaj atın 

- `!dusk`  yazın 
- Cüzdanınızı yazın

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/2544c3d0-7066-4dee-a621-53e46022fe12)


- Aşağıdaki komutu girin ve cüzdan kelimelerinizi yazarak giriş yapın.
- Şifrenizi belirleyin
- Şifre tekrar girin

```shell
rusk-wallet restore
```
![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/3c4397d7-d700-4895-89b1-093bf847ae51)


- konsensüs anahtarını dışarı aktarmak için aşaıdaki komutu girin
- Cüzdanınızın şifresini girin
- Tekrar Şifrenizi girin

```shell
rusk-wallet export -d /opt/dusk/conf -n consensus.keys
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/144a1e46-7cb4-41b7-9362-3b68528b1015)

- Şifrenizi girin

```shell
sh /opt/dusk/bin/setup_consensus_pwd.sh
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/fc75a806-b717-4141-a612-668bde4e88d8)

- Servisi Çalıştırın

```shell
service rusk start
```

- Loglara bakın Bu şekilde akıyorsa sorun yok demektir. son bloğa ulaşmadan stake yapmayın

```shell
tail -F /var/log/rusk.log
```

```shell
grep "block accepted" /var/log/rusk.log
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/cf2e32ec-d550-4c35-b467-d9ae9fbc20b9)


## Stake işlemleri

- Son bloğa ulaşmadan stake yaparsanız görünmez o yüzden loglara bakın ondan sonra stake yapın. Son blok kontrol https://explorer.dusk.network/
- Cüzdanınıza Faucet üzerinden 1000 tDusk aldıysanız aşağıdaki komutu girerek stake işlemini başlatın

```shell
rusk-wallet stake --amt 1000 # Or however much you want to stake
```

- Stake sonrası aşağıdaki gibi bir ekran gelecek 30 block onayı verecek

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/9a32e710-d070-4fb9-a893-351e64e5a70a)



- Stake bilgilerinizi kontrol edin

```shell
rusk-wallet stake-info
```

- Böyle görünmesi lazım

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/9a572b65-100a-4341-aa70-9ba87a425623)


## Senkronizasyon Kontrol

Aşağıdaki kodu direk sunucuya yapıştırın bloklar yükseliyormu kontrol edin.

```shell
curl --location --request POST 'http://127.0.0.1:8080/02/Chain' --header 'Rusk-Version: 0.7.0-rc' --header 'Content-Type: application/json' --data-raw '{
    "topic": "gql",
    "data": "query { block(height: -1) { header { height } } }"
}' | jq '.block.header.height'
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/c7bfb3eb-d46f-499b-9be8-64fa3b4411f9)


## Destek

Core Node ekibine teşekkürler.

