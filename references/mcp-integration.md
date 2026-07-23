# MCP 集成与降级策略

## MCP 工具对照表

| # | 类别 | 常见 MCP 名称 | 用途 | 降级方案 |
|---|------|--------------|------|---------|
| 1 | 地图 | `mcp__google-maps` / `mcp__amap` | 路线规划、距离计算、交通时间 | WebSearch 估算 |
| 2 | 火车票 | `mcp__rail` / `mcp__12306` | 车次查询、票价、余票 | WebSearch 查询参考 |
| 3 | 机票 | `mcp__flight` / `mcp__skyscanner` | 航班时刻、价格对比 | WebSearch 查询参考 |
| 4 | 天气 | `mcp__weather` / `mcp__openweather` | 目的地天气预报 | WebSearch 历史趋势 |
| 5 | 汇率 | `mcp__exchange` / `mcp__currency` | 国际旅行货币换算 | WebSearch 近期汇率 |

## MCP 检测方法

检查系统提供的 function list 中是否存在 `mcp__` 前缀的工具名称，按上表类别匹配：

1. 列出所有 `mcp__*` 工具
2. 对照上表 5 个类别逐一归类
3. 对缺失类别，准备安装建议

## 批量询问模板

检测完毕后，一次性呈现结果：

```
MCP 环境检测完成：
✅ 已就绪：地图（amap-mcp）、天气（openweather-mcp）
⚠️ 缺失：
  - 火车票 MCP — 可查询实时车次和票价
  - 机票 MCP — 可查询实时航班和价格
  - 汇率 MCP — 国际旅行预算换算

是否需要安装以上 MCP？输入编号选择（如 "2,3"），或回复"跳过"全部使用搜索降级。
```

## 降级标注规范

| 数据来源 | 标注 | 含义 |
|---------|------|------|
| MCP 工具获取 | ✅ 实时数据 | 当前可用的准确数据 |
| WebSearch 获取 | 📌 参考数据，建议出行前核实 | 搜索结果，可能过时 |

## MCP 安装指引

用户选择安装某个 MCP 时：

1. 使用 `WebSearch` 搜索 `"<MCP名称> claude code mcp server install npm"`
2. 提供安装命令和配置 JSON 片段
3. 不自动执行安装，由用户操作完成后确认
