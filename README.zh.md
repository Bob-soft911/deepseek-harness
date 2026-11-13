# DeepSeek Harness

[English](README.md) | 中文
update 
DeepSeek Harness（`dsh`）是由 [DeepSeek AI](https://deepseek.com) 开发的开源 agent harness（智能体框架）。

它构建于**一切皆插件**的架构之上，由 [Cordis](https://github.com/cordiverse/cordis) 驱动，其设计参见论文 [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512)。

文档：[https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## 项目功能

DeepSeek Harness 可运行可配置的 AI Agent，用于检查和编辑工作区文件、执行 Shell 命令、搜索和获取网页内容，也可以把任务委派给子 Agent。会话会持久保存历史记录，方便用户继续工作和回顾过程。

不同 Profile 为这些能力提供不同入口：交互式 Web UI、一次性无界面任务、TypeScript 和 Python SDK 集成，或通过 ACP 接入自动化客户端。插件支持按需选择模型、工具、执行提供方和权限策略；[架构指南](docs/architecture.zh.md)介绍这些部分如何组合。

## 典型使用场景

- **代码库开发：**理解项目代码、编辑文件、运行检查，并在工作区内协同处理多步骤改动。
- **研究与知识工作：**在持久会话中搜索和获取网页内容，或通过 MCP 连接外部服务。
- **工作流集成：**从终端或脚本运行一次性任务，通过 SDK 将 Agent 接入应用，或连接 ACP 自动化宿主。
- **专用 Agent：**围绕工作流所需的模型、工具和执行策略组合 Profile 与插件。

## 选择使用入口

| 入口 | 适用场景 |
|---|---|
| Web UI | 通过浏览器工作区和设置进行交互式会话。 |
| Headless Profile | 从终端或自动化任务运行一次性工作。 |
| TypeScript 或 Python SDK | 将 Agent 会话集成到应用中。详见 [Python SDK 指南](docs/user/guide/python-sdk.zh.md)。 |
| ACP Profile | 通过 Agent Client Protocol 连接自动化客户端。 |
| Desktop 应用 | 使用打包的桌面应用。 |

工具访问和执行行为由所选 Profile 的配置、沙箱和审批策略控制。运行 DSH 前请阅读[安全说明](SAFETY.zh.md)。

## 开发者预览

DeepSeek Harness 处于 _开发者预览_ 阶段，正在快速迭代。**未来将出现破坏兼容性的变更。**

运行本项目前，请阅读[安全说明](SAFETY.zh.md)。

<a id="run"></a>

## 运行

### 通过 `npm` 运行

安装 `Node.js`，然后运行：

npx @deepseek-ai/dsh web

该命令默认会在 `http://127.0.0.1:3080` 启动 Web UI，本机启动时还会用默认浏览器打开页面。通过 SSH 启动时只打印宿主机 URL，因为本地转发地址由 SSH 客户端或编辑器持有。传入 `--no-open` 可仅运行服务器而不打开浏览器。详见 [Web UI 指南](docs/user/guide/index.zh.md)。

<a id="run-from-source"></a>

### 从源码运行




如需从仓库源码运行：

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` 会准备仓库产物。`pnpm dsh web` 会直接使用这些已构建产物，不会重新构建。

## 社区与支持

- 通过 [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions) 提交反馈或 bug 报告。
- 为你的插件仓库添加 [`dsh-plugin`](https://github.com/topics/dsh-plugin) 话题，便于被发现。
- 欢迎加入 DeepSeek Harness 企微群！扫描下方二维码填写入群问卷，小助手会定期发送入群邀请。

<table>
  <thead>
    <tr>
      <th align="center">入群问卷</th>
      <th align="center">微信公众号</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><a href="https://trtgsjkv6r.feishu.cn/share/base/form/shrcnIt5twSVdLGD52KJBckGCgg"><img src="https://cdn.deepseek.com/harness/readme/community-wecom-survey.png" alt="DeepSeek Harness 入群问卷二维码" width="180" height="180"></a></td>
      <td align="center"><img src="https://cdn.deepseek.com/harness/readme/community-wechat-official-account.png" alt="DeepSeek Harness 团队微信公众号二维码" width="180" height="180"></td>
    </tr>
  </tbody>
</table>

## 参与贡献

参见 [CONTRIBUTING.md](CONTRIBUTING.zh.md)。

## 开发

请先阅读[开发指南](docs/development.zh.md)与[架构文档](docs/architecture.zh.md)。

`pnpm run dev:web` 会在一个终端里完成构建、启动，并在源码修改时重建 client bundle；`make help` 列出 Web 与 Desktop 对应的 Make target。完整表格见开发指南的「应用命令」一节。

面向 agent：请遵循 [AGENTS.md](AGENTS.md)。

## 引用

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## 许可证

[MIT](LICENSE)

第三方依赖及其许可证见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
