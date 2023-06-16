# Taiko

- [Official Docs](https://taiko.xyz/docs/guides)
- [Twitter](https://twitter.com/taikoxyz)

[DISCORD](https://discord.gg/taikoxyz)

[![dev chat](https://discordapp.com/api/guilds/984015101017346058/widget.png?style=banner2)]([https://discord.gg/taikoxyz])


## Siapkan Dapp Sepolia

[Aclhemy](https://dashboard.alchemy.com/)

[Infura](https://app.infura.io/login)

- Copas WSS & HTTPS

<p align="left"><img height="auto" width="auto" src="https://user-images.githubusercontent.com/98658943/227556609-c0fe2742-cc1c-4322-9a83-3de0def97a2d.png"</p>


## Install Alat dan Bahan ( Jika belum )

Docker

```
sudo apt update; sudo apt upgrade
```

```
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```


## Clone Repo

```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd ~/simple-taiko-node
```

## Edit .env

```
cp .env.sample .env
```

Lalu edit
```
nano .env
```

Paste https dan wss dari Alchemy tadi kesini
<p align="left"><img height="auto" width="auto" src="https://user-images.githubusercontent.com/98658943/227559350-8362428d-3fc6-4e14-8c2d-fea6b484f2bb.png"</p>

### (Optional)

- Prover

Bisa aktifkan `Prover` kalo spek nya mencukupi [ 8/16 core CPU dan 32GB  RAM ]. Jika spek mencukupi, silahkan aktifkan `Prover`
Ubah `false` menjadi `true` lalu paste Private Key wallet baru kalian
  
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/95b77f5f-28f4-44f6-82b4-67b9a367f463"</p>


- Proposer

Mengaktifkan proposer diperlukan token [TKKO](https://explorer.test.taiko.xyz/address/0x7b1a3117B2b9BE3a3C31e5a097c7F890199666aC) . Cara mendapatnya belum dijelaskan [Disini](https://taiko.xyz/docs/guides/receive-tokens).

 Untuk persiapan, bisa di atur terlebih dahulu, cukup ganti `false` ke `true` dan paste Private Key di kolom Private Key lalu Wallet Address di kolom Address.

<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/799cbc63-f28e-40bf-927b-190a39d64d8c"</p>

**Jika sudah memiliki TKKO**

1. Pergi ke Contract Taiko di Sepolia [Disini](https://sepolia.etherscan.io/address/0x6375394335f34848b850114b66A49D6F47f2cdA8#writeProxyContract)
2. Connect menggunakan wallet yang sama untuk node
3. Pilih `depositTaikoToken`
4. Masukan jumlah token yang ingin di depostikan, misal ingin deposit 10 maka isi dengan `1000000000`
5. Klik Write dan approve di metamask

# RUN!

```
docker compose up -d
```

## Command lain-lain

### Cek logs

```
cd ~/simple-taiko-node
docker compose logs -f
```

### Cek logs `Prover` kalo di aktifin

```
cd ~/simple-taiko-node
docker compose logs -f taiko_client_prover_relayer
```

### Cek logs L2 Engine

```
cd ~/simple-taiko-node
docker compose logs -f l2_execution_engine
```

### Cek stats

buka link ini di browser kalian, ganti `IPVPS` ke IP VPS mu
  
```
http://localhost:3000/d/L2ExecutionEngine/l2-execution-engine-overview
```

Contoh:

`http://192.168.1.1:3000/d/L2ExecutionEngine/l2-execution-engine-overview`

#


Jika ada error seperti ini saat mengecek logs
`Fatal: Failed to register the Ethereum service: database contains incompatible genesis`

Coba untuk hapus kemudian ulang

```
docker compose down -v
```

lalu

```
docker compose up -d
```

Jika ingin me restart node

```
cd ~/simple-taiko-node
docker compose restart
```

#

<div id="header" align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMzNmZTIxZmE3ZmY3MzRiMDcwNDJhYTQ5ZmNlY2YxMWE1OWIyYmVkNSZlcD12MV9pbnRlcm5hbF9naWZzX2dpZklkJmN0PWc/mVBlqOD4ra9jQiI3cC/giphy.gif" height="125" width="420"/>
</div>
