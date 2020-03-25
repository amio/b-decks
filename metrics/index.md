
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

## Navigation Timing

---

![](https://www.w3.org/TR/navigation-timing-2/timestamp-diagram.svg)

> [Processing Model: 28 steps](https://www.w3.org/TR/navigation-timing-2/#processing-model)

<style>
img {width: 100vw }
</style>

---

https://data.bytedance.net/aeolus#/dataQuery?rid=205890&appId=2933

---

## Inspect `processing`

Steps 21 - 24:

- domInteractive
- domContentLoadedEventStart
- domContentLoadedEventEnd
- domComplete

---

## Paint

- first-contentful-paint `FCP`
- largest-contentful-paint `LCP`

---

## FCP (99 percentile)

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

## LCP

> Largest Contentful Paint:
>
> the render time of the largest content element visible in the viewport.

---

### Please Define LCP

- What elements are considered?
- How is an element's size determined? 
- When is largest contentful paint reported?

---

#### elements

  - `<img>`
  - `<image>` (svg)
  - `<video>` 的 poster image
  - 有 `background: url()` 属性的元素
  - 包含文本节点的块级元素

---

#### size

- 处于 viewport 内的部分
- overflow: hidden 的部分不算在内
- 图片：`min(原始大小, 显示大小)`













