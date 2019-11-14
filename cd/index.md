# 持续部署

FAST @ ALL SCALE

---

# Chapter 1

---

## 持续集成 (c-integration)
## 持续交付 (c-delivery)
## 持续部署 (c-deployment)

---

![](https://files-7t1ohuuw4.now.sh)

---

### how
### *now.sh*
### works

---

### https://simpleicons.now.sh

```
$ now ls simpleicons

$ now alias
```

<!--
```
   +-----------+
   | fpmsxrvqp |    simpleicons-fpmsxrvqp.now.sh      simpleicons.now.sh
   +-----------+                                      simpleicons.simple.now.sh
                                                      simpleicons-git-master.simple.now.sh
   +-----------+                                      simpleicons-git-now-v2.simple1.now.sh
   | i69f4uvi9 |    simpleicons-i69f4uvi9.now.sh      simpleicons-amio.simple1.now.sh
   +-----------+

   +-----------+
   | jgdfxizn5 |    simpleicons-jgdfxizn5.now.sh
   +-----------+

   +-----------+
   | ......... |
   +-----------+
```
-->

---

![](https://files-7t1ohuuw4.now.sh)

---

# ZEIT Main Site

- docs & dashboard

- branch: master (c-dep)

---

# ZEIT Now Cli

- canary (c-del)
  - (c-dep: latest-now-cli)

- master (c-del)

---

# canary + beta phase

---

# ADV: FAST PACE

早收益，早反馈，早改进

---

# ADV: OWNERSHIP

"you build it, you run it"

  -- Werner Vogels, 2006

_[ACM: A Conversation with Werner Vogels](https://queue.acm.org/detail.cfm?id=1142065)_

---

## Amazon

- 一年 5000 万次部署
- 每个工程师每天部署超过 50 次
- 研发人员承担（大部分）测试和（应用）运维

---

## DevOps!
(2009)

---

# ADV：CONFIDENCE

代码库存 ➤ 交叉感染几率 ➤ 发布风险

---

# ADV：SCALE UP

代码库存 ➤ workflow 包袱 ➤ 管理成本

---

## facebook

- 混合模式（weekly + daily*3）

- 每天 1000+ diff on master，每周 10000+ (2016-)

- 每天 1000+ 部署 (2017+)

---

# CASE STUDY：facebook

[Rapid release at massive scale](https://engineering.fb.com/developer-tools/rapid-release-at-massive-scale/)

[Continuous Deployment at Facebook and OANDA](https://research.fb.com/publications/continuous-deployment-at-facebook-and-oanda/)

[Continuous Deployment of Mobile Software at Facebook (Showcase)](https://research.fb.com/publications/continuous-deployment-of-mobile-software-at-facebook-showcase/)

---

![](https://engineering.fb.com/wp-content/uploads/2017/08/GF0oPwHBDYx4GjgBAAAAAAAQG0oVbj0JAAAB.jpg)

branches & releases (before 2016)

---

### a true continuous push system would
### deliver every individual change to production
### soon after it landed

---

![](https://engineering.fb.com/wp-content/uploads/2017/12/GIYNPgGn5SctXdIGAAAAAAAkALkybj0JAAAB.jpg)

branches & releases (after 2017)

---

quasi-continuous “push from master”

---

### Advantages

- 不再需要 hotfix
- 更好支持全球团队
- 推动研发下一代工具、自动化、流程
- 用户体验更好，更快

---

### 移动端

![](https://engineering.fb.com/wp-content/uploads/2017/08/GCwoPwH2OwiJGfwGAAAAAAD_s_x5bj0JAAAB.jpg)

CI

---

### 每个修改的生命周期

![](https://engineering.fb.com/wp-content/uploads/2017/08/GFOkQQFUfKKF2PEAAAAAAACQDy1Pbj0JAAAB.jpg)

Andoird: 50,000 ~ 60,000 builds / day

---

### 4 -> 2 -> 1

![](https://engineering.fb.com/wp-content/uploads/2017/08/GCNMQAEuyGOwD7wAAAAAAADgzcRpbj0JAAAB.jpg)

real world test: engineers -> daily canary -> 1m beta testers

---

团队 **x20**

代码 **x50**

**生产力** 和 **质量** 保持不变

---

![](https://files-mo529i0ig.now.sh)

---

![](https://files-m963y1jbo.now.sh)

---

开发者**偏爱**更快的发布节奏

---

![](https://files-nh7t4psjr.now.sh)

---

# OANDA

- 100 engineers
- 货币交易系统（数十亿/天）
- 自用 / 白标

---

### ONADA 白标（观察1）

- 产品劣势
  - 低优先级的问题会持续几个月得不到修复
  - 新功能推出慢

---

### ONADA 白标（观察2）

- 开发体验
  - 每次部署包含上千个修改 -> 焦虑 -> 重量级测试
  - 问题发现延迟 -> 上上周我干了什么？

---

# Chapter 2

---

## All Scale

- simpleicons
- ZEIT
- ONADA
- Baixing
- Amazon, Facebook, Etsy, Flickr, Google, Netflix

---

# <span style="font-size: 1.5em">极致</span>

> 字节范儿

---

## Thanks