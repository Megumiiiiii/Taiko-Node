# Taiko

- [Official Docs](https://taiko.xyz/docs/guides)
- [Twitter](https://twitter.com/taikoxyz)

[DISCORD](https://discord.gg/taikoxyz)

[![dev chat](https://discordapp.com/api/guilds/984015101017346058/widget.png?style=banner2)]([https://discord.gg/taikoxyz])



## Deploy Smart Contract menggunakan Remix

### Prepare segala keperluan

1. Buka Remix
[DISINI](https://remix.ethereum.org/)

2. Atur jaringan Taiko, pergi ke [Chainlist](https://chainlist.org/?testnets=true&search=Taiko) lalu tambahkan Taiko (Alpha-3 Testnet)

3. Bridge ETH Sepolia ke Taiko
[Disini](https://bridge.test.taiko.xyz/)

Request Sepolia: [Alchemy](https://sepoliafaucet.com/) [Infura](https://www.infura.io/faucet/sepolia)

### Mulai membuat Contract

1. Setelah semua siap, kembali ke remix
2. Buat file baru dengan cara klik icon ini, beri nama `simple.sol` atau apapun yang penting `.sol`
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/7122db47-6f9b-4e12-97ad-361b78d85324">

3. Lalu copy Code ini
```
pragma solidity ^0.8.2;

contract TestToken {
    mapping(address => uint) public balances;
    mapping(address => mapping(address => uint)) public allowance;
    uint public totalSupply = 1000000 * 10 ** 6;
    string public name = "Test Token";
    string public symbol = "TEST";
    uint public decimals = 6;
    
    event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);
    
    constructor() {
        balances[msg.sender] = totalSupply;
    }
    
    function balanceOf(address owner) public returns(uint) {
        return balances[owner];
    }
    
    function transfer(address to, uint value) public returns(bool) {
        require(balanceOf(msg.sender) >= value, 'balance too low');
        balances[to] += value;
        balances[msg.sender] -= value;
       emit Transfer(msg.sender, to, value);
        return true;
    }
    
    function transferFrom(address from, address to, uint value) public returns(bool) {
        require(balanceOf(from) >= value, 'balance too low');
        require(allowance[from][msg.sender] >= value, 'allowance too low');
        balances[to] += value;
        balances[from] -= value;
        emit Transfer(from, to, value);
        return true;   
    }
    
    function approve(address spender, uint value) public returns (bool) {
        allowance[msg.sender][spender] = value;
        emit Approval(msg.sender, spender, value);
        return true;   
    }
}
```

4. Paste ke file tadi
5. Edit nama Contract, nama Token, dan Symbol Token
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/734211cb-cd79-4d37-84e6-17edfe021362">

6. Buka `Compiler` disini
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/627b1dd5-f232-4eb4-bc33-214988058362">

7. Pilih `0.8.12` lalu *compile*. Abaikan warn
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/99a42094-3ad5-4ea4-9e4d-189df67493c7">

8. Setelah di *compile*, pergi ke bagian *deployer*
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/e3dc23cb-0c25-4d98-91f2-3afa518500c8">

9. Pilih `Injected Provider` lalu hubungkan ke Metamask. Pastikan Metamask mu sudah menggunakan jaringan `Taiko Alpha-3 Testnet`
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/12e0be8f-7aa6-4268-96fd-a6306f82c618">

10. Klik Deploy
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/c9d12c85-d9e8-45c2-8d77-ff11bb812fcf">

11. Approve di Metamask
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/0eed8d1e-e85e-4c80-98fe-0036279acbec">

12. Setelah terkonfirmasi, buka txhash tadi. Lalu klik SC mu
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/5032e311-8237-47ae-b260-f8b8985afbb3">

13. Pergi ke bagian `Code`
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/85c74394-d2a2-4a3c-a033-f9c836bbd175">

14. Pilih **Verify & Publish**
!<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/094505fe-9dcf-42a5-a258-b3e23b83067b">

15. Pilih `flattened`
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/b6236cb7-e8bd-44a1-a48d-5599b7c21dff">

16. Masukan nama Contract
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/80be4f68-9b30-4172-aac3-337d66459332">

17. Pilih `0.8.12` **WAJIB**
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/3ef6c077-3f3c-4c5c-8686-b750591ebe12">

18. Copy semua code mu di remix
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/92dadb52-7615-487b-95bc-ed1e31064891">

29. Optimiziation pilih `No`. Lalu paste code mu kesana. Dan `Try to fecth..` pilih `Yes`
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/f1a541fb-254e-42c8-8de4-d5a2f6164063">

## DONE!
<p align="left"><img height="auto" width="auto" src="https://github.com/Megumiiiiii/Taiko-Node/assets/98658943/f6e5602f-1cb9-4f5a-9b67-b6c464156de6">


#


<div id="header" align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMzNmZTIxZmE3ZmY3MzRiMDcwNDJhYTQ5ZmNlY2YxMWE1OWIyYmVkNSZlcD12MV9pbnRlcm5hbF9naWZzX2dpZklkJmN0PWc/mVBlqOD4ra9jQiI3cC/giphy.gif" height="125" width="420"/>
</div>





























