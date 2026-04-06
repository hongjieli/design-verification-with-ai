# RegMatrix

面向 register / spec intelligence 的设计验证辅助方向。

## 问题定义

寄存器验证表面上结构化程度很高，但现实里依然很痛苦：

- spec 文档和实现细节分散在 PDF、表格、注释、脚本中
- register field 之间的依赖、约束和 side effect 不总是显式写清楚
- 手工把 spec 变成测试点和约束模型很费时间
- 很容易漏掉 mode interaction、reset behavior、access policy 等角落

## 为什么 AI 有帮助

这一类问题非常适合“半自动 intelligence”而不是纯自动生成：

- spec 和 register map 通常带有一定结构
- 可以抽取 field、access type、dependency、reset value 等信息
- 可以把文档语言转成更接近验证动作的候选建议

## 核心思路

**RegMatrix** 是一个面向寄存器与规格文档的智能层，它负责：

- 解析 spec / register 描述
- 提取 field 关系、dependency、约束与行为模式
- 组织成更适合 DV 使用的结构化关系图
- 给出测试建议、corner case 建议与覆盖建议

## 典型输入

- register spec / CSR 文档
- field 描述、access policy、reset value
- YAML / XML / IP-XACT / 内部表格导出
- 已有 RAL model 或寄存器脚本
- 相关 feature requirement

## 典型输出

- field dependency graph
- 可疑的 spec 模糊点或冲突点
- 候选测试场景
- 可派生的约束关系
- 建议补充的 checker / coverage point

## 例子：AI 可辅助的能力

- “这个 enable bit 与 mode field 联动，建议补充 mode 切换下的 write/readback 测试。”
- “这些字段共享 reset dependency，但文档描述不一致。”
- “这个只读字段看起来会被另一个 status event 间接影响，建议验证 side-effect update。”
- “根据 access type 和 dependency，建议补上 illegal access 与 reset-after-write 两类测试。”

## 工程挑战

- spec 文字经常模糊、不完整，甚至自相矛盾
- 不是所有 dependency 都能靠文本直接抽出来
- 需要避免把它包装成“全自动理解规格”的过度承诺
- 输出结果必须方便工程师验证和修改，而不是黑盒生成

## 评估指标

- 能否发现真实遗漏的寄存器测试点
- 是否减少手工阅读和整理 spec 的时间
- 是否提升 register verification completeness
- 工程师是否愿意把输出结果纳入现有 RAL / test planning 流程

## References

### 学术参考

- AI / ML for hardware verification 的综述与邻近工作
- 文档抽取、关系图构建、constraint generation 相关研究

### 工程 / 工具参考

- UVM 1.2 Reference Documentation — <https://verificationacademy.com/verification-methodology-reference/uvm/docs_1.2/html/index.html>
- IP-XACT / register metadata workflows
- PyVSC / NetworkX 等适合表达约束和依赖图的工程库

## 为什么这个方向值得做

RegMatrix 是个很强的 topic，因为 register verification 已经足够结构化，适合做部分自动化；同时它又足够痛，团队能明显感受到“多一层智能整理”带来的价值。