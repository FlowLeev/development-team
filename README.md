# development-team

一个面向非简单软件改动的 Agent Skill。它解决的不是“agent 不会写代码”，而是 agent 在理解现有系统、边界和约束之前就开始修改，随后依靠连续补丁弥补早期设计缺失的问题。

核心流程只有三道门：**理解 → 决策 → 证据**。八个角色文件是按需加载的方法库，不要求每个任务机械走完一套团队仪式。

## 适用范围

适合：

- 新功能、Bug 修复和行为变更
- 跨模块重构、迁移与系统集成
- 可能影响公共契约、持久化数据、安全边界或运行方式的配置修改

不适合：

- 只读解释或独立代码审查
- 拼写、格式化和其他不需要调查或设计的机械编辑

## 安装

将本仓库放入 Agent 已注册的 skills 目录。例如：

```bash
git clone git@github.com:FlowLeev/development-team.git ~/.dsh/skills/development-team
```

其他兼容 Agent Skills 的客户端，请将仓库放入其 skills 目录，或注册本仓库父目录。客户端应先发现 `SKILL.md` 的 `name` 与 `description`，选中后再加载完整正文和所需 references。

## 让所有非简单代码改动都先考虑本 skill

自动选择依赖模型根据 description 做路由，不能当作绝对保证。如果希望它成为默认开发纪律，可在项目级或全局 agent 指令中加入：

```markdown
对于任何非简单的软件功能、Bug 修复、重构、迁移、集成或配置变更，
在第一次写入前加载 development-team skill。
纯机械编辑、只读解释和独立代码审查不触发。
```

这条短规则负责稳定路由；完整工作方法仍保留在 skill 中，避免长期占用上下文。

## 目录

```text
development-team/
├── SKILL.md                # 触发条件与三道门主流程
├── references/
│   ├── sizing.md           # 风险分档
│   ├── roles-map.md        # 角色来源与边界
│   └── hats/               # 八个按需角色
└── evals/evals.json        # 行为评测用例
```

## 许可证

[MIT](LICENSE)
