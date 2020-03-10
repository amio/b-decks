# Aeolus OnPremise

>frontend

---

## 私有化部署

> 给你三台物理机，搭个风神出来。  
> 不联外网的。

---

### 问题 / 需求

- 解除对内功能依赖
  - 静态资源依赖 CDN
  - 功能依赖内网 SDK
- 解除网络依赖
  - 部署 / 运行

---

## Thanks to 南京团队

---

## 前端的工作

1. 对内解耦

2. 差异化处理

---

## 对内解耦

- 在线加载的 SDK
  - 需要的（Polyglot、IconFont）
    - 改为编译期打包进项目
  - 不需要的（消息中心、反馈）
    - 改为 JS 动态加载，用 feature flag 控制
- 静态资源引用走相对路径，而非 CDN 地址

---

## 差异化处理

- __差异化 Config__（针对各种环境编译对应的打包结果）
  - config replacement / build env + tree shaking
- __差异化 Serve__（同一份编译结果，不同环境输出不同内容）
  - Node.js Server + Statics
- __Dockerize__（完整功能，标准封装）
  - 和后端解耦，独立编译、测试和部署（技术、流程）
  - 更好的复用（更多第三方场景、其他业务的私有化场景）
---

## 运行时处理
  - Docker `RUNTIME = saas`  
    => 差异化 serve（config，sourcemap）  
    => html `__env__: { RUNTIME: 'saas' }`
  - More Capability

---

### Write Once, Run Anywhere

---

Write Once,__（Build Everywhere）__Run Anywhere

---

## Build Once, Run Anywhere

---

## 部署架构

---

![](aeolus-onpremise/full.png)  

---

![](aeolus-onpremise/frontend.png)  
_集群中的前端_

---

### TODO

- SaaS MVP => 私有化部署
- 没有测试环境，没有发版流程
- 编译和部署流程全手工，需要提高自动化程度
- 可复用的 Docker Image（最佳实践、开发友好）

---

### QA
