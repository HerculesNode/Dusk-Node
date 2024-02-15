# Dusk Node işlemleri

Dusk teşvikli Node kurulum işlemi. Ödül alabilmeniz için;  
- 20 Şubat itibarıyla düğümlerin çalışır durumda olması gerekiyor. Bu, "sayıldığı" ve çalışma süresinin kaydedileceği zamandır
- 20 Şubat - 15 Mart 2024 arası çalışması gerekiyor.


## Linkler
 * [Hercules Telegram](https://t.me/HerculesNode)
 * [Hercules Twitter](https://twitter.com/Herculesnode)

## Sistem özellikleri

Önerilen : 
- Sunucu alacak arkadaşlar kurulum sırasında UBUNTU 22.04 seçmeli
- UBUNTU 22.04
- 4 RAM
- 50-100 GB SSD

## Sistem Güncelleme ve kütüphaneler
```shell
sudo apt update && sudo apt upgrade -y
```

## Rust kurulumu yapın  

Kurulumu yapın

```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.0/itn-installer.sh | sudo sh
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/5ee16ea6-6e42-4bba-b3ed-caeb52759a05)


## Cüzdan oluşturma ve Faucet işlemi 

- Bu adrese gidin ve cüzdan oluşturun https://wallet.dusk.network/setup/

- Cüzdan adresinizi kopyalayın ve Twitter adresinizden Tweet atın. Cüzdan adresi ve sonuna $DUSK #ITN  bu şekilde.

- Faucet gidin ve twitter linkinizi kopyalayın https://faucet.dusk.network

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/c8bc06fe-9814-4540-bef1-fa0f1ed5f970)

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/e234b68b-5fd9-4906-b9b6-368fc10f2961)

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

- Loglara bakın Bu şekilde akıyorsa sorun yok demektir.

```shell
grep "block accepted" /var/log/rusk.log
```

![image](https://github.com/HerculesNode/Dusk-Node/assets/101635385/cf2e32ec-d550-4c35-b467-d9ae9fbc20b9)


## Stake işlemleri

- Cüzdanınıza Faucet üzerinden 1000 tDusk aldıysanız aşağıdaki komutu girerek stake işlemini başlatın

```shell
rusk-wallet stake --amt 1000 # Or however much you want to stake
```

- Stake bilgilerinizi kontrol edin

```shell
rusk-wallet stake-info
```
