# 2026-09-16 源码保存与暂停交接

用户因暂时没有时间继续开发，要求将当前版本代码保存到 GitHub。本文件记录当前工作副本，方便恢复工作；不把源码保存当作实现验收、部署或运行授权。GitHub 上传是否完成，以实际远程提交核对结果为准。

## 保存范围

- 当前源码、测试、依赖声明及锁文件、项目说明、设计与治理文件。
- 保留尚未验收的 formal weather bridge R1，未执行 R2。
- 排除 `.env` 和本机环境文件、虚拟环境、node_modules、本地 Codex 配置、backups、data、outputs、日志及缓存。
- 本归档仅保存代码和文档，不是整机或研究数据备份。`data/` 中的采集数据、审计原始输出和测试所需本地探针仍在原工作区；部分测试依赖这些数据及本机路径，不能保证从源码归档直接运行全部测试。

## 最近完成的局部工作

2026-09-14 已闭合 capture publication 到正式输入的身份映射，形成桥接候选并完成一次 R1。候选文件：

- `tools/research_multi_city_v1/formal_weather_bridge.py`
- `tests/research_multi_city_v1/test_formal_weather_bridge.py`

该轮历史验证记录：作者套件由 QA 独立重跑 8/8 通过，旧 adapter 回归 4/4 通过；首轮七项 P1 已关闭，R1 最终独立 QA 仍为 FAIL，剩余两项 P1。2026-09-16 保存操作不重跑这些测试，也不把历史测试结果描述为今日新测试。

## 恢复工作时的两项局部阻断

1. **R1-P1-01：合法原始温度的量化兼容性。** 现行采集规则将 numeric `25.3456` 量化为 `25346` 毫摄氏度；R1 `_observation_milli` 却要求原始值乘 1000 已为整数，额外拒绝该合法记录。应消费按现行规则核验的整数毫摄氏度，再精确构造 Decimal，保留 bool、非数值和非有限值拒绝。
2. **R1-P1-02：WeatherOL effective 与报告分钟绑定。** WeatherOL 的 `source_time` 按现行规范为 null；R1 的 effective 对应检查跳过了此分支。应核对现行 capture 使用的 observed 本地日期加报告分钟、超过 observed+5 分钟回退一天的规则，不新增来源 UTC 时间定义。

上次提出的后续方案是一次 R2：DATA 修正最多 20 分钟、独立 QA 最多 20 分钟、T00 局部评审最多 10 分钟。此前尚未取得第二次返修授权；此次 GitHub 保存请求仅授权保存动作，不自动执行 R2。

## 状态和本机证据

- 当前局部桥接未验收，正式自动模拟目标仍未完成。
- 未由此次保存请求启动真实采集、模型、服务、部署、Paper/Live、订单或资金操作。
- 既有 M010、M017、M007 待确认及真实消费、训练、报告、资格等依赖继续保留，以当前 TASK_CONTRACT 入口和明确用户指令为准。
- 基础 HEAD（保存提交之前）：`13ca49c39ffe6cff4a75c23c3233af7cbd6cfaac`。
- 本机详细证据（不包含在源码归档的 data 目录）：`data/reports/formal_weather_bridge_publication_closure_20260914.md` 及 `data/reports/formal_weather_bridge_20260914/qa_r1/`。

保存前 R1 源码身份为 `3d844d7a36bdae897567b4689362e765413d5b380eb2cb5072874476c280dfc4`，专属测试身份为 `6302c6825fea7bb12a64282e5a0d7ad6800bfc6be1cb02b42471f3707e7fd433`。归档清单另记录实际保存文件的 SHA-256。
