# 智能体兼容性

本方法依赖普通文件、可阅读的 Markdown 和明确的协作约定，而不是某一家产品的插件。不同智能体对目录访问、工具权限、项目规则和会话持久性的支持不同；规则是否生效还需在实际会话验证。

| 环境 | 起步方式 | 边界 |
|---|---|---|
| Codex | 打开工作台目录；Codex 支持项目 `AGENTS.md`。必要时发送通用启动指令 | 规则发现路径、权限和版本影响实际行为 |
| WorkBuddy | 打开或授权访问工作台目录，发送通用启动指令并确认已读规则 | 官方在项目级“代码开发”配置中提及兼容根目录 `AGENTS.md` 和 `CODEBUDDY.md`；并不证明所有模式自动加载，未完成实机验收 |
| Claude Code | 在工作台目录使用 `CLAUDE.md` 入口，或发送通用启动指令 | 模板使用引用指向 `AGENTS.md`；具体生效需核对版本及权限 |
| GitHub Copilot | 在受支持的仓库场景使用 `.github/copilot-instructions.md` 入口，或发送通用启动指令 | 规则支持因客户端和功能而异；模板入口不保证调用工具读取文件 |
| 其他可读写文件的智能体 | 打开目录，发送通用启动指令；根据实际工具能力执行 | 逐一测试读取、创建、修改和恢复，不推断所有产品兼容 |
| 仅聊天的智能体 | 手动粘贴内容，并手动保存输出 | 不能直接完成文件操作 |

官方参考：[Codex 项目规则](https://developers.openai.com/codex/guides/agents-md/) · [WorkBuddy 项目说明](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Project) · [Claude Code 项目记忆](https://code.claude.com/docs/en/memory) · [GitHub Copilot 自定义指令](https://docs.github.com/en/copilot/concepts/prompting-and-context/custom-instructions)。

## 建议做的四个小测试

1. 让智能体报告当前工作目录并指出根规则中的一条具体规则。
2. 创建一个虚构的测试项目，确认输入、过程和输出分层。
3. 让它对一种交付从经验索引选读，并说明选了哪些类别。
4. 重新打开会话，要求它根据项目 README 接续；验证它实际读取了状态。

每个测试记录产品、版本、环境、权限、日期和结果。无需向公开仓库上传测试中的私人内容。
