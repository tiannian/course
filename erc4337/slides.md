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

---

## 一个新的交易池

### 签名聚合

### 原子操作

--- 

## 合约自定义鉴权

### UTXO Script

### 其他算法

### 门限签名 / 多签名

### 中心化认证

### Zk Proof认证

---

## 自定义手续费

- 先付原生
- 之后交易返还

---

## 隐私支持

### 避免隐私交易手续费泄露地址

### Proof证明所有权

---

## 账户

### 直接收款

