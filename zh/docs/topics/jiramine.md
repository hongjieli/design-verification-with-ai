# JiraMine

基于 JIRA / bug 历史记录，挖掘最容易暴露真实 RTL bug 的 testcase、feature 组合与回归场景。

## 问题定义
很多团队积累了大量 JIRA 缺陷记录，但这些历史数据通常没有真正反哺 regression 策略。实际情况往往是：有些 testcase、sequence、配置组合会反复发现有价值的 RTL bug，而另一些 testcase 只是长期消耗算力。

## AI 能做什么
AI 可以把 bug 文本、失败 testcase、模块标签、owner、root-cause、resolution 历史串起来，找出“历史上最容易发现真 bug”的 case pattern，而不是只看单次 fail 数量。

## 核心思路
**JiraMine** 可以：
- 关联 JIRA ticket 与 failing tests、feature、module、regression context
- 找出 bug yield 明显更高的 testcase / 场景
- 区分一次性偶发问题和长期高价值的找 bug 模式
- 给 smoke / sanity / priority regression 推荐更高价值的 tests
- 解释为什么某个 test 被判定为“高价值找 bug case”
