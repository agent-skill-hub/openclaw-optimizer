# openclaw-optimizer

> 你的 OpenClaw 实例每天在烧多少钱？大概率，比你以为的多 10 倍。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 这是什么

一个专门给 **OpenClaw（自托管 Claude）** 做"体检 + 手术"的 Skill。

装上它，Claude 会帮你把实例从"能跑"调到"跑得好、花得少、不漏风"——Token 成本、性能瓶颈、安全漏洞，一次全扫。

## 为什么重要

先看一笔账：

```
Token spend = (input + output) x calls/day x model price
```

| 场景 | 每次多花 | 每天 100 次调用 | 一个月下来 |
|------|---------|----------------|-----------|
| workspace 里多了 1000 tokens 冗余 | 微不足道？ | 10 万 tokens | **~$45**（Sonnet） |
| 没开 Prompt Caching | 每次重复发送上下文 | 全价重复计费 | **多花 10 倍** |
| tools.profile 没设 full | 工具静默失效 | 你以为在用，其实没用 | **无法估算的隐性成本** |

大多数人的 OpenClaw 实例，就像一辆没做过保养的车——能开，但油耗惊人，还有几个灯没亮。

## 它帮你做什么

| 类别 | 做的事 | 效果 |
|------|-------|------|
| **Token 审计** | 扫描 workspace 每个文件的 token 消耗，精简到最低 | 立省真金白银 |
| **性能调优** | Prompt Caching / Context Pruning / Compaction | 重复上下文费用降 90% |
| **功能修复** | tools.profile 设 full、Gemini 搜索替代 Brave、非英文记忆召回修复 | 工具真正能用起来 |
| **安全加固** | macOS 防火墙、gateway 绑 loopback、token 认证、文件权限审计 | 不给外部留口子 |
| **模型切换** | Opus / Sonnet 按需切换策略 | 重活用 Opus，轻活用 Sonnet |

## 谁应该装

- 已经跑起来 OpenClaw 但没仔细调过的人（大多数人）
- 每月账单看着肉疼但不知道从哪下手的人
- 把安全放在心上但不想自己一条条查的人

## 快速安装

```bash
npx skills add agent-skill-hub/openclaw-optimizer -g -y
```

装完之后，在 Claude Code 里直接说：

```
帮我优化 OpenClaw 实例
```

Skill 会引导你一步步完成审计和优化。

## 和 SKILL.md 的关系

README 只告诉你"是什么"和"为什么"。

所有技术细节、操作步骤、配置参数都在 **SKILL.md** 里——那才是 Claude 真正读的"手术手册"。你不需要自己去读它，Claude 会照着做。

## 推荐搭配

| Skill | 为什么搭配 |
|-------|-----------|
| **proactive-agent** | 让 Claude 主动发现问题，而不是等你问 |

## License

MIT — 随便用，改了更好的欢迎 PR。
