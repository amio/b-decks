# Perf Metrics

Kudos to `PerformanceObserver`

---

## Measure, Optimize & Monitor

> performance workflow

---

## Factors

- Networks
- User Agents
- Quantile (50, 90, 99)

__Lab__ _vs_ __Field__

---

## 分析方式

- 基于时间的趋势变化（发现问题、衡量效果）
- 一段时间内指标的分布（理解性能状况）
  - 内容分组（子路径）
  - 指标分布（[TTI 直方图](https://data.bytedance.net/aeolus#/dataQuery?rid=212464&appId=2933)）

---

## 数据准确度

- 浏览器保证（原生实现，最高精度）
- 时间无关（加载前发生的事件也统计得到）
- 排除极值（关注有效数据）

---

## 20% Faster

---

## Overview

- 资源加载（navigation）：`Navigation Timing`
- 渲染（paint）：`FCP`, `LCP`
- 交互（interactive）：`FID`，`TTI`
- 持续运行期间：`longtask`

---

## Navigation Timing

---

![](/perf-metrics/navigation-timestamp.svg)

> [Processing Model: 28 steps](https://www.w3.org/TR/navigation-timing-2/#processing-model)

<style>
img { width: 100vw }
</style>

---

https://data.bytedance.net/aeolus#/dataQuery?rid=205890&appId=2933

---

## Inspect `processing`

- domInteractive
- domContentLoadedEventStart
- domContentLoadedEventEnd
- domComplete

[Steps 21 - 24](https://www.w3.org/TR/navigation-timing-2/#processing-model)

---

## Paint

- first-contentful-paint `FCP`
- largest-contentful-paint `LCP`

---

## FCP (P99)

- 0 - 2s FAST
- 2 - 4s OK
- over 4s SLOW

_[lighthouse score](https://web.dev/first-contentful-paint/#how-lighthouse-determines-your-fcp-score)_

---

https://data.bytedance.net/aeolus#/dataQuery?rid=205543&appId=2933

---

我们的指标建议

- FCP (P90) < 5s

---

## Largest Contentful Paint
>
> The render time of the largest content element visible in the viewport.
>
> 视窗内最大可见内容元素的渲染时间。

---

### Please Define LCP

- Elements: 不是所有元素都平等地算数
- Size: 如何计算有效面积？
- When: 什么时候触发？

---

#### Elements

  - `<img>`
  - `<image>` (svg)
  - `<video>` 的 poster image
  - 有 `background: url()` 属性的元素
  - 包含文本节点的块级元素

---

#### Size

- 处于 viewport 内的部分
- overflow: hidden 的部分不算在内
- 图片：`min(原始大小, 显示大小)`
- 文本：包含文本节点的最小矩形区域
- 所有元素的 margin、padding、border 不算在内

---

#### When / mechanism

- 页面一开始渲染马上触发第一个 lcp
- 每当有更大的 paint item 出现就触发一个新的 lcp
- 持续到用户首次交互（click / scroll / input）

---

#### When

- 官方示例
  - `visibilitychange`
- 我们的策略
  - `min(scroll, mousedown, keypress, 120s, v..e)`

---

#### 建议标准

- 建议：(75P) 2.5s 以内
- 我们：(50P) 4s 以内

---

https://data.bytedance.net/aeolus#/dataQuery?rid=209344&appId=2933


---

## First Input Delay

FCP 👫 FID

> 从用户首次交互（点击、输入等）到浏览器做出响应的时间

---

### Long FID

- 主要由主线程 blocking 导致
- 通常发生在 FCP（first contentful paint）和 TTI（time to interactive）之间

---

### 为什么格外关注第一次的延迟

- 第一印象的影响更大
- 主要的问题发生在加载期间
- 优化 __FID__ 的解决方案和优化 __后续输入延迟__ 有所不同

---

### 如何分析 FID

> （无交互 / 短延迟 / 长延迟）

- 关注：95-99 分位数据（涵盖大多数不良体验的情况）
- 区分设备类型（如桌面端和移动端设备）
- 建议指标：小于 100ms（75P）
- 我们的建议指标：小于 150ms（90P）

---

https://data.bytedance.net/aeolus#/dataQuery?rid=203146&appId=2933

---

## Time To Interactive

> 从页面加载开始，  
> 到主要资源加载完成、能够立刻响应用户交互的时间点

> https://web.dev/tti/

---

### Define TTI

1. 把 __First Contentful Paint (FCP)__ 作为起始点

2. 向后寻找一段 __5s__ 的 __Quiet Window__  

   空闲窗口定义是：这段时间没有发生 __long task__ 事件，并且有活动的网络 GET 请求不超过两个。

3. 从这段空闲窗口再向前找到最近一次 __long task__，如果没有的话以 FCP 为准。

4. TTI 就是__空闲窗口之前最后一次 long task 的结束时间__（如果没有 longtask 的话就等于 FCP 时间）

---

![](perf-metrics/tti-timeline.svg)

<style> img { height: 80vh } </style>

---

### 取舍

尽早渲染内容 _vs_ 尽早支持交互

> Case Study: SSR vs CSR

---

### 指标

- 建议指标：5 秒以内（一般移动设备）
- 我们的建议指标：10 秒以内（75P）

---

https://data.bytedance.net/aeolus#/dataQuery?rid=208532&appId=2933

https://data.bytedance.net/aeolus#/dataQuery?rid=212464&appId=2933

---

## long task

> Long task refers to any of the following occurrences whose duration exceeds 50ms: ……  
>
> -- [w3c longtask spec](https://w3c.github.io/longtasks/#sec-terminology)

> （不负责翻译：主线程阻塞超过 50ms 的时间片）

---

- 耗时 90/95 分位
- count / navigation

https://data.bytedance.net/aeolus#/dashboard/39220?appId=2933

---

## One More Thing

---

### 自定义指标

- `performance.mark()`
- `performance.measure()`

---

```js
performance.mark('marker-a')
performance.mark('marker-b')

performance.measure('start_to_now')
performance.measure('a_to_now', 'marker-a')
performance.measure('a_to_b', 'marker-a', 'marker-b')
```

---

Aeolus preQueryCalculate_time
https://data.bytedance.net/aeolus#/dataQuery?rid=215501&appId=2933

---

## PERF METRICS

> by Perfu

---

## 三分钟接入，第二天看数

> Speed of Perfu

---

# [WIKI](https://bytedance.feishu.cn/wiki/wikcnKYopZkFKr2DeyyhOyi4vrg) &nbsp; • &nbsp; [CODE](https://code.byted.org/dp/perf-watcher) &nbsp; • &nbsp; Lark 

<style>
.slide {
  background: url(/perf-metrics/kill-bill.jpg) center;
  background-size: cover;
}

* { color: white !important }
a:hover { color: red !important; text-decoration: none !important }
</style>
