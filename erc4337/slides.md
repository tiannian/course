---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# ERC4337 账户抽象(Account Abstraction)

---

## Standard of Ethereum

- EIP: Ethereum Improvement Proposal
- ERC: Ethereum Request for Comment

---

## Account Type

- EOA 外部账户
- CA 合约账户

---

## 问题？特性

<br/>

### EOA

- 限定了只有secp256k1的账户体系
- 用户管理私钥
- 难以迁移到其他生态，绑定Metamask等。

<br/>

### CA

- 没有直接操作接口，需要间接通过EOA完成
- 鉴权模式比较简单
  - `msg.sender`
  - `tx.origin`

<br/>

### 如何区分？

- `account.code` ?
- 未部署的合约账户与普通账户没有区别

---

## 解决问题

<br/>

> 没有什么问题是不能通过增加一个抽象层来解决的

<br/>

- 自定义鉴权方式
- 统一账户方式
- 不修改现在的共识层(安全与历史问题)
- 去中心化(命根子)

--- 

##  可能的好处

<br/>

- 隐私交易： 避免手续费泄露地址
- 原子化多操作： (create2 redeploy问题)
- 自定义Token支付手续费
- 聚合签名，降低gas费
- 复杂且多样化的鉴权方式

## 可能的问题

<br/>

- 生态影响(现有ERC的鉴权方式需要调整，或者再增加一个抽象层)

---

## 架构与方案

![EIP4337](https://user-images.githubusercontent.com/10502431/223316557-27b3e312-d2d7-42f6-b5a9-0b1eaf0c0a8f.png)

- 内存池
- 一组合约

---

## 一个新的交易池

### 签名聚合

具有线性特性的签名可以进行聚合。聚合后整个Bundler只需要验证一个签名。

支持算法：

- Schnorr
- BLS

---

## 一个新的交易池

- 解除原有交易池限制。
- 支持不同种交易池实现。
- 支持可以以调整的原子交易范围。

--- 

## 自定义鉴权

### 合约鉴权方案

- 通过原生功能鉴权： `msg.sender` `tx.origin`
- 通过签名：`ecrecover`

### UTXO Script

- P2PK
- P2PKH
- P2SH

---

## 自定义鉴权

### 多种方式算法

- 支持其他签名算法
- 支持门限签名 / 多签名
- 支持中心化认证
- 支持Zk Proof认证

---

## 自定义手续费

- 先付原生
- 之后交易返还

> 这有个流程图

---

## 隐私支持

- 避免隐私交易手续费泄露地址
- Proof证明所有权

---

## 抽象的账户模型

这有结构体

---

## 抽象的账户模型

### 初次收款

> 这有流程图

