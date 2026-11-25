# ToolSense

让 AI 在需要可靠结果时，主动选择合适的工具。

比如你说「从 1 到 100 随机选一个整数，只告诉我数字」。加载 ToolSense 后，Agent 应先用当前环境的随机数生成器抽一次，再只回复抽到的数字。如果无法执行，它应如实说明。

| 你的请求 | ToolSense 的处理方式 |
| --- | --- |
| 随机抽签、精确计算、计数排序、解析数据、计算哈希、验证代码输出 | 调用适合的工具，检查结果后回答 |
| 查询当前事实，或核对论文、文件中的说法 | 优先查看权威来源，说明证据和适用范围 |
| 起名、润色、头脑风暴 | 通常直接回答 |

在一次 Codex 对照中，相同的抽数请求得到了两种行为。未加载技能的会话直接回答了一个数字。显式加载的会话调用了一次 JavaScript 随机数生成器，回复与工具输出一致。这次测试验证了显式加载后的一个实例，自动触发率和跨平台表现仍待测试。[查看测试记录](tests/observations.md)

## 安装与使用

将仓库内容放进宿主支持的技能目录，文件结构应为 `toolsense/SKILL.md`。下载仓库 ZIP 后，可以把解压出的顶层文件夹改名为 `toolsense`。在支持显式调用的 Codex 会话中输入 `$toolsense 从 1 到 100 随机选一个整数` 即可试用。宿主决定何时加载技能以及可以使用哪些工具。

## English

ToolSense is a portable Agent Skill for choosing tools when computation, external evidence, or execution can make an answer more reliable. It does not install tools or force a host to invoke them.

## Install

Copy the `toolsense` folder into a skill directory recognized by your agent. For Codex, a user-level location is `~/.codex/skills/toolsense/`; a project-level location may be `.agents/skills/toolsense/` when supported by your setup. Other hosts may use a different skills directory or import procedure.

## Activate

Reload or restart the host if it caches skills. Invoke it explicitly as `$toolsense` where supported, or make it available to the host's normal skill discovery. Automatic selection varies by product and configuration. Merely copying the folder does not guarantee it will be loaded for every turn.

## Contents

- `SKILL.md`: tool selection and evidence rules.
- [Behavioral cases](tests/cases.md) and [observed Codex results](tests/observations.md).

## Limitations

ToolSense can only use tools exposed and permitted by the current host. It cannot create a Python runtime, browse the web, or force execution by itself. When a required capability is absent or fails, the agent should disclose the limitation and avoid claiming an unperformed action.
