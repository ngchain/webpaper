title: NGIN - Decentrailized Application Engine based on Blockchain Ecosystem
speaker: NGO
url: https://github.com/ngchain
prismTheme: tomorrow
plugins:
    - echarts
    - mermaid
    - katex

<slide class="bg-white aligncenter">

# ![NGIN](/NG.png)

# Decentrailized Application **Engine**  {.text-shadow}
# based on Blockchain Ecosystem {.text-shadow}

---

**NGIN** is pronounced "engine" {.text-intro}

[:fa-github: Github](https://github.com/ngchain){.button.ghost} 
[:fa-git: Gitea](https://code.ngin.cash){.button.ghost}
[:fa-server: Deamon](https://github.com/ngchain/ngcore){.button.ghost}
[:fa-money: Wallet](https://github.com/ngchain/hawkhover){.button.ghost}


<slide class="bg-white aligncenter">

:::div {.content-left}

## Features {.text.text-shadow}

---

:::card 
- **Fast ignition**
- Less, or **no storage cost**(mem only)
- With **humanizing** account model, users can send tx with **memorable short number**
- **High security** with Sheet and Vault(Block) model
- Powerful and scalable types of tx
- Support **Multi-Tx**, sending coins to different recipants in the same time
- Powerful **WebAssembly** VM support based on account state(contract)
- Contract is **more maintainable** than ethereum
- **Libp2p(ipfs)** powered p2p networking 
- Available **anonymous** address for saving balance
- Using the **schnorr signature**, allowing Multi-Sig when sending and receiving
- **Fee Destory Policy** keeps the mainnet coin NG's value
- Using swagger style **restful API**, be friendly to the developers

:::

![](/davinci.png)

> "**NGIN** is the best public PoW chain yet.”
> ==Leonardo da Vinci==

<slide class="bg-white aligncenter">

## Structure {.text-shadow}

---

```mermaid
sequenceDiagram
    WASM ->> Account: apply account state.
    Account->>Sheet: constitute
    Sheet->>Block: summarize and hash.
    Block->>Chain: link up
    Block->>P2P: broadcast

    Chain->>P2P: sync

    loop bcast
        P2P->>P2P: recv chain and txs
    end

    P2P->>Chain: recv sync

    P2P->>Block: recv block
    Block->>Sheet: apply new txs and check all account states
    Sheet->>Account: apply transaction, assign and append tx
    Account->>WASM: call event

```

<slide class="bg-white aligncenter">

:::div {.content-left}

## ngCore

---

ngCore is the third daemon on NGIN。

Concurrently, the ngBiz is a new try for union chain based on ngCore's codebase, within which we use PBFT replacing PoW consensus.

:::

:::div {.content-right}
The first two versions are ngind(based on go-ethereum) and ngd/ngdaemon(published on internal git repo not github)
Initially, NGIN project was aiming to build **an internet serach engine**(like google) ecosystem based on blockchain
But ngind was soon deprecated due to the origin Russian team's plan.
And then ngd/ngdaemon's team continued their project but then it was also deprecated before releasing because of the team broke up.
Some codes of ngd/ngdaemon are inherited by ngcore when ngcore starts, but now all be placed by new codes.

From the view of codebase, ngcore is **not a fork of any project**. Currently, ngcore has implemented all core functions of a blockchain public chain, like p2p network protocol, memory-safe VM based on WebAssembly, etc.

Now, ngcore is on alpha period.

:::
:::

<slide class="bg-white aligncenter">

:::div {.content-left}

![](/preview_light.png)

:::

:::div {.content-right}

### Hawkhover

---

Hawkhover a multi-platform GUI wallet for NGIN daemon, which is designed by dart and flutter and can be installed on Windows/Linux desktop, Android and iOS.

Hawkhover will be released after ngcore's beta period
:::

<slide class="bg-white aligncenter">

:::div {.content-right}
![](/preview_dark.png)
:::

<slide class="bg-white aligncenter">

## Diff between **BTC** & NGIN

--- 

- Goal of NGIN, not creating any crypto currency or building a new payment method, is maintaining a decentrialized application engine with reliable blockchain ecosystem
- Using number account, not garbled string. So more convenient.
- Using Schnorr signature，not ECDSA: [Schnorr vs ECDSA](https://bitcoin.stackexchange.com/questions/77234/schnorr-vs-ecdsa)
- No half-life period, NGIN using Fee Destory Policy to keep the value of mainnet coin.
- ... 


<slide class="bg-white aligncenter">

## ## Diff between **ETH** & NGIN

---

- Goal of NGIN, not creating token ecosystem, is maintaining a decentrialized application engine with reliable blockchain ecosystem
- NGIN suggests non-financial decentralized applications like spiders, storages and webservices etc.
- Using number account, not garbled string. So more convenient.
- Using Schnorr signature，not ECDSA: [Schnorr vs ECDSA](https://bitcoin.stackexchange.com/questions/77234/schnorr-vs-ecdsa)
- No EVM，and NGIN assembles more common WebAssembly VM, with which developers can create their app with asm.js, rust, kotlin, c, c++ etc.
- ...

<slide class="bg-white aligncenter">

---

```mermaid
stateDiagram
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]

// not supported by nodeppt yet
```
