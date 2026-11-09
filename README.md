### kira905

#### 这是什么

> 做 **Agent 系统** 的产品人。我在意的事很小也很具体：**让一个长期跑在电脑里的 AI 助手，能被普通人装上、用得稳、坏了能自己修。**

---

#### 它解决什么

现在大多数「AI 助手」的寿命是一个会话 —— 关上窗口就忘干净，进程一崩没人知道为什么，改坏一个配置只能重装。

我在 **DeepSeek Harness（DSH）** 这套 Agent 运行时上，把它做成能长期活着的东西：任务看板、长期记忆、巡检自愈、长会话交接、改动回滚 —— 出问题能打印一份「现场报告」交给别人。

做出来的是 **27 个公开仓 / 22 个已发布 npm 包**，**零第三方运行时依赖**（装一个包只需要 node，不会顺带拖进一棵依赖树）。

---

#### 一条命令跑起来

每个仓的安装都只有一行，例如：

```powershell
npm i -g @kira905/dsh-butler-core
```

装完叫什么名字、怎么确认真装上了、哪条命令只读哪条会写盘 —— 各仓 README 的「一条命令跑起来 / 装完自检」两节都写清了，照抄就行。

---

#### 三个代表作

**🧭 [dsh-butler-core](https://github.com/kira905/dsh-butler-core)** — 常驻调度与自律闸门

Agent 要长期活着，难的从来不是「能干活」，而是**知道什么时候该干、什么时候不该干**。这里有常驻调度器、自主授权矩阵（哪些动作可以自己拍、哪些必须等人点头）、通知、日报，以及一条**哈希链审计**：每条自主动作都有出处、可追溯、能熔断。

`npm i -g @kira905/dsh-butler-core`

**🧠 [dsh-memory-toolkit](https://github.com/kira905/dsh-memory-toolkit)** — 记忆引擎

会话一结束就遗忘，是 Agent 最像「工具」、最不像「同事」的地方。这里有一套独立实现的记忆引擎：向量召回 + FTS5 关键词双路、**命中留痕**（能回答「这条记忆为什么被捡回来」）、分层软淘汰（搬走不等于删），外加一整套只读体检器具。

`npm i -g @kira905/dsh-memory-toolkit`

**🚑 [dsh-firstaid](https://github.com/kira905/dsh-firstaid)** — 急救台

Agent 真的会坏：起不来、假死、改坏了要撤销、数据被误删。四类现场压成**一个入口**，默认只读，产出**能整段交给别人的现场报告** —— 这是「敢让非工程背景的人用」的前提。

`npm i -g @kira905/dsh-firstaid`

---

#### 还值得一看

| 仓 | 一句话 |
|---|---|
| [dsh-session-toolkit](https://github.com/kira905/dsh-session-toolkit) | 长会话的自动交接：把「聊到一半」的事实采集成可交接的档 |
| [dsh-quality-toolkit](https://github.com/kira905/dsh-quality-toolkit) | 把工程规矩做成检查器（24 个入口），口径不靠人记 |
| [dsh-ops-toolkit](https://github.com/kira905/dsh-ops-toolkit) | 备份 / 快照 / 受控升级 / 插电保护 |
| [dsh-peer-toolkit](https://github.com/kira905/dsh-peer-toolkit) | 多机协同：加密信箱、选路、文本同步、按需隧道 |
| [dsh-life-toolkit](https://github.com/kira905/dsh-life-toolkit) | 人生记忆：把旧会话原文建成可召回的索引 |
| [dsh-task-board-local](https://github.com/kira905/dsh-task-board-local) | 任务看板插件：一张卡 = 一次真实会话，跑完由人验收 |
| [ops-handoff-design](https://github.com/kira905/ops-handoff-design) | 📖 11 份设计记录（脱敏）—— 这套东西为什么这么设计 |

---

#### 什么是开源的、什么不是

上面这些仓是**能直接装、能自己改的工具与检查器**。有两块**不在这一批里**：

- **「自己盯着活干」的那套引擎** —— 定时调度、队列盯守、管家日报、自主决定要不要动手。这批正在陆续放（已经开出去的是调度内核 [`dsh-butler-engine`](https://github.com/kira905/dsh-butler-engine)）。
- **「出事喊到人」的通道** —— 企业微信、语音播报这类：**不随开源发布**。

整套东西的**设计是公开的**：[`ops-handoff-design`](https://github.com/kira905/ops-handoff-design) 里那 16 份记录写清了它为什么这么设计 —— 想自己实现的人照着做得到。

所以：这里给的是**工具、图纸和纪律**，不是一个会自己上班的管家。

---

#### 几句实话

- 这些**我自己每天在用**，不是 demo。仓里的判据都是能现跑的命令，不是「已测试」三个字。
- 许可 = **AGPL-3.0 + 商业授权**（双许可）。
- 代码主要由 AI 结对产出，**产品判断、口径和验收标准由我定** —— 我做的是「一个 Agent 系统该有什么纪律」，并把它推到能日用的程度。
