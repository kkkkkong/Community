分类机器人
Triagebot（又名 rustbot）是一个通用机器人，用于 rust-lang 组织中的各种任务，通常涉及通过 GitHub 或 Zulip 评论发送命令。 以下页面介绍了可用的功能。

命令通常是通过编写以文本开头的注释来发出的。 可用的命令取决于您正在使用的存储库。 每个存储库都有一个，您可以在其中查看已启用的功能。@rustbottriagebot.toml

例如，以下注释：

@rustbot label A-diagnostics A-macros
将在 GitHub 问题或拉取请求上设置给定的标签，即使对于没有直接权限在 GitHub UI 中执行此操作的人也是如此。

GitHub 命令
关于 GitHub 问题或拉取请求的命令通常是通过编写后跟评论中的任何位置的命令来发出的。 将忽略 Markdown 代码块、内联代码跨度或块引号中的命令。 可以在一条注释中输入多个 rustbot 命令。@rustbot@rustbot

Triagebot 还允许编辑评论。 如果您不修改命令的文本，则 triagebot 将忽略编辑。 但是，如果修改现有命令或添加新命令，则将处理这些命令。

配置
各个 GitHub 仓库可以通过在默认分支的根目录中调用的文件来配置 triagebot 功能。 以下页面介绍了每个功能所需的语法。triagebot.toml

例如，配置文件位于 https://github.com/rust-lang/rust/blob/master/triagebot.toml。rust-lang/rust

首次添加到新存储库时，您需要启用机器人的权限才能运行。 这可以通过将 PR 发布到 rust-lang/team 数据库以添加到目录中的存储库来完成。triagebot.tomlbots = ["rustbot"]repos/rust-lang


常用命令摘要
以下是您可能会在 rust-lang/rust 上看到的一些常见命令。

命令	描述	文档
@rustbot claim	将问题分配给自己。	问题分配
@rustbot release-assignment	删除对议题的分配。	问题分配
@rustbot assign @octocat	将问题分配给特定用户。	问题分配
@rustbot ready	指示 PR 已准备好进行评审。	快捷方式
@rustbot author	表示 PR 正在等待作者。	快捷方式
@rustbot blocked	表示 PR 在某项上被阻止。	快捷方式
@rustbot label A-diagnostics A-macros	为议题或 PR 添加两个标签。	标签
@rustbot label -P-high	从议题或 PR 中删除标签。	标签
@rustbot ping windows	发布一条评论，对 Windows ping 组执行 ping 操作。	Pinging（平安）
@rustbot prioritize	请求优先级排序工作组确定优先级。	确定优先级
r? @octocat	将 PR 分配给用户。	PR任务
r? libs	分配给 libs 评审组中的随机人员。	PR任务
r? rust-lang/cargo	从货运团队中随机分配一名人员。	PR任务
以下是您可能会在 Zulip 上看到的一些常见命令：

命令	描述	文档
@triagebot read	等待人们在会议中阅读文档。	Zulip 会议管理
@triagebot end-topic	检查每个人是否都完成了会议中的主题讨论。	Zulip 会议管理
@triagebot end-meeting	检查每个人是否都准备好完成会议。	Zulip 会议管理
实现
可以在 https://github.com/rust-lang/triagebot 上找到 triagebot 的源代码。 如果您对扩展 triagebot 感兴趣，那里的文档应该提供一些有关如何开始的指导。