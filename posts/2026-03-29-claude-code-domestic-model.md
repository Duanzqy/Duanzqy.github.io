---
layout: default
title: How to Use Claude Code with Domestic Models
description: A Chinese draft on using Claude Code on Windows through WSL and connecting it to MiniMax API.
---

# Windows 上如何使用 Claude Code，并接入 MiniMax API

这篇文章记录一个比较实用的方案：在 Windows 上通过 WSL 使用 Claude Code，并将模型接到 MiniMax API，使用 `MiniMax-M2.7` 系列模型。对于日常写代码、读项目、做命令行辅助来说，这是一套比较顺手的本地工作流。

## 1. 为什么在 Windows 上使用 Claude Code 需要 WSL

Claude Code 本质上是一个面向命令行环境的开发工具，它的默认体验更接近 Linux / macOS 这样的 Unix 环境。在 Windows 上，虽然也能使用终端，但很多 Node 工具、Shell 工作流、路径行为和依赖安装方式，实际上在 WSL 中更稳定，也更接近官方和社区默认假设的运行环境。

所以如果你在 Windows 上想稳定使用 Claude Code，最省心的做法通常不是硬在原生 Windows 终端里折腾，而是直接进入 WSL。

### 什么是 WSL

WSL 全称是 Windows Subsystem for Linux，可以理解为 Windows 提供的一层 Linux 运行环境。安装之后，你可以在 Windows 里直接运行 Ubuntu 等 Linux 发行版，使用熟悉的 Linux 命令行、包管理器和开发工具链。

它不是传统意义上笨重的虚拟机，但又能提供非常接近真实 Linux 的开发体验，因此对终端型开发工具非常友好。

### 为什么推荐用 WSL

对 Claude Code 这种以终端为中心的工具来说，WSL 的优点很明显：

- 环境更接近官方默认支持的 Linux 使用方式
- Node.js、npm、git、ssh 这类工具在 WSL 里通常更稳定
- Shell、路径、权限、软链接等行为更符合常见开发文档
- 更容易复用社区里大多数教程和脚本
- 与 VS Code、Windows Terminal、GitHub 等工具链集成已经比较成熟

简单说，如果你主要是想把 Claude Code 当成一个稳定的命令行编程助手，WSL 通常比原生 Windows 方案更少踩坑。

## 2. 在 WSL 中安装 Claude Code

下面以 Ubuntu 为例。

### 第一步：安装 WSL

如果你还没有安装 WSL，可以先在管理员 PowerShell 中执行：

```powershell
wsl --install
```

安装完成后，按提示重启电脑。第一次启动 Ubuntu 时，需要设置一个 Linux 用户名和密码。

安装好之后，可以先确认当前环境：

```bash
uname -a
```

如果输出中包含 Linux 内核信息，说明 WSL 环境已经可用。

### 第二步：在 WSL 中安装 Node.js

Claude Code 依赖 Node.js 生态，因此先准备好 Node 和 npm。最直接的做法是安装 `nvm`，再通过它安装较新的 Node LTS 版本。

例如：

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

重开终端后，安装 Node：

```bash
nvm install --lts
nvm use --lts
```

检查版本：

```bash
node -v
npm -v
```

### 第三步：安装 Claude Code

在 WSL 终端里安装 Claude Code。具体安装命令可能会随着版本变化而更新，所以建议优先参考 Claude Code 官方文档里的最新安装方式。

如果当前版本通过 npm 安装，通常会是类似下面的形式：

```bash
npm install -g @anthropic-ai/claude-code
```

安装完成后，检查命令是否可用：

```bash
claude --version
```

如果能正常输出版本号，说明 Claude Code 已经在 WSL 中安装成功。

## 3. 接入 MiniMax API，并使用 minimax2.7 模型

这一部分的关键是先搞清楚 Claude Code 当前支持怎样的 API 接入方式。不同时间点，Claude Code 可能默认依赖 Anthropic 官方接口，也可能支持通过兼容层、代理或自定义网关进行接入。

因此实践上你需要确认两件事：

1. Claude Code 当前版本是否允许自定义 API Base URL
2. MiniMax 提供的是哪种兼容协议：Anthropic-compatible 还是 OpenAI-compatible

如果 MiniMax 提供的是兼容接口，那么通常可以通过环境变量或配置文件把请求导向 MiniMax 网关。

### 准备 MiniMax API Key

先在 MiniMax 平台申请 API Key，并确认你要使用的模型名。你这里的目标模型可以写成：

```text
minimax2.7
```

如果平台实际采用的是更完整的模型 ID，需要以 MiniMax 控制台或官方文档中的名称为准。

### 在 WSL 中配置环境变量

可以先把 API Key 写进 `~/.bashrc` 或 `~/.zshrc`。例如：

```bash
export MINIMAX_API_KEY="your_api_key_here"
export MINIMAX_MODEL="minimax2.7"
```

如果 Claude Code 支持自定义接口地址，还可以进一步设置：

```bash
export OPENAI_API_KEY="$MINIMAX_API_KEY"
export OPENAI_BASE_URL="https://your-minimax-compatible-endpoint"
export OPENAI_MODEL="$MINIMAX_MODEL"
```

或者如果它走的是 Anthropic 兼容接口，则可能会类似：

```bash
export ANTHROPIC_API_KEY="$MINIMAX_API_KEY"
export ANTHROPIC_BASE_URL="https://your-minimax-compatible-endpoint"
export ANTHROPIC_MODEL="$MINIMAX_MODEL"
```

这里最重要的是：具体变量名必须以 Claude Code 当前版本支持的配置方式为准，MiniMax 这一侧也要以它提供的兼容接口说明为准。不同版本之间，这部分配置细节可能会变化。

### 验证是否接通

配置完成后，可以先重开终端，再进入一个测试项目目录中运行 Claude Code，观察它是否能正常发起请求。

你至少可以检查下面几件事：

- 命令是否正常启动
- 是否识别到模型配置
- 首次请求是否返回正常结果
- 是否出现认证失败、模型名错误或接口协议不兼容等报错

如果一切正常，就说明 Windows + WSL + Claude Code + MiniMax 这一套链路已经基本打通。

## 4. 一些进阶设置

在基础可用之后，还可以做一些进一步优化，让日常使用更顺手。

### 4.1 把项目放在 WSL 文件系统中

如果你长期在 WSL 里开发，建议把项目直接放在 Linux 文件系统里，例如：

```text
~/projects/your-project
```

而不是总是在 `/mnt/c/...` 下操作。这样通常会有更好的文件访问性能，也更少遇到权限和路径问题。

### 4.2 配合 VS Code Remote - WSL

如果你习惯图形化编辑器，推荐使用 VS Code 的 Remote - WSL 插件。这样你可以：

- 在 Windows 上打开 VS Code 界面
- 实际在 WSL 里运行终端、Node、git 和 Claude Code
- 获得更一致的 Linux 开发体验

这是 Windows 用户最常见、也最舒服的一种组合。

### 4.3 用 shell 配置文件统一管理 API 变量

如果后面还会切换不同模型提供商，建议把环境变量集中写到 Shell 配置文件里，并加上注释。例如：

```bash
# MiniMax
export MINIMAX_API_KEY="your_api_key_here"
export MINIMAX_MODEL="minimax2.7"
```

以后切换提供商时会清晰很多。

### 4.4 为常用命令写别名

如果你经常在固定配置下启动工具，可以给 Shell 写别名，例如：

```bash
alias cc='claude'
```

这样日常启动会更快。

### 4.5 记录常见报错

这类工具最容易踩坑的地方通常有：

- Node 版本不兼容
- npm 全局安装路径未加入 `PATH`
- API Key 未生效
- Base URL 配置错误
- 模型名与平台真实名称不一致
- 实际接口协议和工具预期不一致

建议把自己遇到过的错误和解决方法都记在这篇文章末尾，后面复用价值会很高。

## 5. 小结

在 Windows 上使用 Claude Code，比较推荐的路径是先进入 WSL，再在 Linux 环境里安装和配置。这样做的核心目的不是“为了复杂而复杂”，而是为了获得一个更稳定、更接近主流开发工作流的命令行环境。

如果你还希望接入国产模型服务，那么关键点就在于确认 Claude Code 当前支持的配置方式，以及 MiniMax 提供的兼容 API 协议。只要这两边能对上，使用 `minimax2.7` 这样的模型做日常开发辅助是完全有机会跑通的。

后续我还会继续补充更具体的配置截图、环境变量示例，以及实际踩坑记录。
