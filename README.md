# Polymarket 天气研究系统

天气市场研究与决策系统的当前源码保存版本，公开供查看与后续开发接续。项目尚未完成，不应把此快照视为实现验收、生产就绪或盈利验证。
基础架构搭好了。欢迎各位大神来继续完成这个bot吧
## 获取完整源码

下载 [polymarket-weather-source-20260916.zip](polymarket-weather-source-20260916.zip)，解压后即可得到完整的 **259 个文件**及原有目录结构。归档包含源码、测试、依赖声明及锁文件、原始 README、设计与审查文档、任务契约和问题记录。

本次通过 GitHub 网页保存源码归档；仓库根目录仅展示归档和交接说明，源码目录在 ZIP 内。GitHub 插件写入返回 `Resource not accessible by integration`，本机 Git 缺少 HTTPS helper，因此尚未将源码逐文件展开为 Git 工作树。

- 保存日期：2026-09-16（Asia/Shanghai）
- 归档大小：1,618,596 字节
- 归档 SHA-256：`641377774e9cd263450db3cdb362881a139c33a5be9f6f1e2f6a6526204a254b`
- 归档内 259 个文件已逐项核对 SHA-256。

## 接续开发

先阅读 [PROJECT_PAUSE_20260916.md](PROJECT_PAUSE_20260916.md)，再查看解压后的 `TASK_CONTRACT.md` 当前状态入口、`CURRENT_ISSUES.md` 和 `项目索引.md`。原始 README 保留了早期阶段记录，须与最新交接说明一起阅读。

formal weather bridge R1 仍有两项已记录的 P1 问题：合法温度量化兼容性，以及 WeatherOL effective 与报告分钟的对应检查。此次保存没有执行 R2 修复，也没有重新运行历史测试。

## 保存边界

不包含实际 `.env`、密钥、数据库、原始采集数据、`data/` 中的审计输出、备份、虚拟环境、依赖安装目录、日志、缓存或原 Git 历史。部分测试依赖原工作区中的数据和本机路径，不能保证解压后直接运行全部测试。

此次操作仅保存和公开当前代码及文档，没有启动采集、模型、服务、部署、Paper/Live、订单或资金操作。
