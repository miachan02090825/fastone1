# Web3 Artifacts Builder 工具套件



## 简介



Web3 Artifacts Builder 是一套强大的工具，用于创建功能丰富的 claude.ai HTML artifacts。该工具套件集成了现代前端技术栈，为开发者提供完整的 Web3 开发环境，支持创建具有钱包连接、区块链交互、国际化等高级功能的单页应用。

## 核心特性



### 🚀 现代前端技术栈



- **React 18** + **TypeScript** - 最新的 React 生态系统
- **Vite** - 快速的开发服务器和构建工具
- **Tailwind CSS** - 实用优先的 CSS 框架
- **shadcn/ui** - 40+ 预配置的现代化 UI 组件

### 🌐 Web3 集成



- **@reown/appkit** - 现代化的钱包连接模态框，支持 MetaMask、WalletConnect、Coinbase Wallet 等
- **viem** - TypeScript 优先的以太坊接口库
- **预配置链** - 支持 Ethereum、Polygon、BSC、Arbitrum、Optimism、Base 等主流 EVM 链

### 🌍 国际化支持



- **react-i18next** - 完整的国际化解决方案
- **多语言支持** - 预配置英文和中文本地化
- **类型安全** - 支持翻译键的自动补全

### 📊 状态管理



- **zustand** - 轻量级、高性能的状态管理库
- **Web3 状态** - 内置钱包连接和区块链状态管理
- **调试支持** - DevTools 集成

### 🛠️ 开发工具链



- **Husky** - Git 钩子，保障代码质量
- **lint-staged** - 只对暂存文件运行代码检查
- **Commitlint** - 强制执行规范的提交信息格式
- **GitHub Actions** - 自动化 CI/CD 流水线
- **Dependabot** - 自动依赖更新和安全警报

## 快速开始



### 步骤 1: 初始化项目



运行初始化脚本来创建新的 React 项目：

```
bash scripts/init-artifact.sh <项目名称>
cd <项目名称>
```



初始化脚本会自动配置以下内容：

- ✅ React + TypeScript 项目结构
- ✅ Tailwind CSS 样式系统
- ✅ shadcn/ui 组件库（40+ 组件）
- ✅ Web3 集成环境
- ✅ 国际化配置（中英文）
- ✅ zustand 状态管理
- ✅ 开发工具链配置
- ✅ GitHub Actions CI/CD
- ✅ Parcel 打包配置

### 步骤 2: 开发 Artifact



在生成的项目中进行开发：

#### Web3 钱包连接示例



```
import { useAppKit } from '@reown/appkit/react'
import { useAppKitAccount } from '@reown/appkit/react'

function WalletConnect() {
  const { open } = useAppKit()
  const { address, isConnected } = useAppKitAccount()

  return (
    <button onClick={() => open()}>
      {isConnected ? `已连接: ${address}` : '连接钱包'}
    </button>
  )
}
```



#### 国际化使用示例



```
import { useTranslation } from 'react-i18next'

function MyComponent() {
  const { t } = useTranslation()

  return <h1>{t('welcome.title')}</h1>
}
```



#### 状态管理示例



```
import { useStore } from '@/store'

function Counter() {
  const { count, increment } = useStore()

  return (
    <div>
      <p>计数: {count}</p>
      <button onClick={increment}>增加</button>
    </div>
  )
}
```



#### 开发工作流



项目配置了完整的代码质量保障：

```
# 提交时会自动运行：
npx lint-staged  # 对暂存文件运行 ESLint 和 Prettier

# 提交信息必须遵循约定式格式：
git commit -m "feat: 添加钱包连接功能"
git commit -m "fix: 修复余额显示问题"
git commit -m "docs: 更新文档说明"
```



支持的提交类型：build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test, wip

### 步骤 3: 打包为单文件 HTML



将完整的 React Web3 应用打包为单个 HTML 文件：

```
bash scripts/bundle-artifact.sh
```



打包脚本会生成 `bundle.html` - 一个包含所有 JavaScript、CSS 和 Web3 依赖的自包含文件，可以直接在 Claude 对话中作为 artifact 分享。

**打包特性：**

- ✅ 环境配置验证（Web3）
- ✅ 优化的打包配置（Parcel 2.12.0）
- ✅ 树摇优化和代码压缩
- ✅ 钱包连接的内容安全策略
- ✅ 资源内联和压缩统计
- ✅ 构建完整性验证

### 步骤 4: 分享 Artifact



将打包生成的 `bundle.html` 文件分享给用户即可。

## 项目结构



初始化后的项目结构：

```
your-project/
├── src/
│   ├── components/     # React 组件
│   ├── hooks/         # 自定义 hooks
│   ├── lib/           # 工具库配置
│   ├── locales/       # 国际化文件
│   ├── store/         # zustand 状态管理
│   └── types/         # TypeScript 类型定义
├── public/            # 静态资源
├── index.html         # HTML 入口文件
├── vite.config.ts     # Vite 配置
├── tailwind.config.ts # Tailwind 配置
├── .env               # 环境变量（需要配置 Reown 项目 ID）
└── package.json       # 项目依赖
```



## 环境配置



### Reown AppKit 配置



在 `.env` 文件中配置你的 Reown 项目 ID：

```
VITE_REOWN_PROJECT_ID=your_project_id_here
```



### 网络配置



工具套件预配置了以下 EVM 网络：

| 网络             | 链 ID |
| ---------------- | ----- |
| Ethereum Mainnet | 1     |
| Polygon          | 137   |
| BSC              | 56    |
| Arbitrum One     | 42161 |
| Optimism         | 10    |
| Base             | 8453  |

## 设计指南



⚠️ **重要**：为避免"AI 风格化"设计，请避免：

- 过度居中的布局
- 紫色渐变
- 统一的圆角设计
- Inter 字体

## 编辑器配置指南



为了获得最佳的开发体验，建议为你的编辑器配置以下设置和扩展。

### Cursor IDE 配置



Cursor 是基于 GPT 的 AI 辅助编程 IDE，特别适合 Web3 开发。

#### 推荐扩展



- **TypeScript and JavaScript Language Features** - TypeScript 支持
- **Tailwind CSS IntelliSense** - Tailwind CSS 自动补全
- **ESLint** - 代码质量检查
- **Prettier** - 代码格式化
- **GitLens** - Git 增强功能

#### Cursor 设置配置



在 `.cursorrules` 文件中添加项目特定的规则：

```
# .cursorrules

## 项目概述
这是一个使用 React + TypeScript + Web3 的前端项目。

## 技术栈
- React 18 + TypeScript
- Vite 构建工具
- Tailwind CSS + shadcn/ui
- Web3: @reown/appkit + viem
- 状态管理: zustand
- 国际化: react-i18next

## 代码规范
- 使用 TypeScript 严格模式
- 遵循 ESLint 配置
- 使用 Prettier 格式化
- 提交信息遵循 Conventional Commits

## Web3 开发指南
- 优先使用 @reown/appkit 进行钱包连接
- 使用 viem 进行区块链交互
- 正确处理异步操作和错误状态
- 支持多链环境

## 设计原则
- 避免过度居中布局
- 不使用紫色渐变
- 避免统一的圆角设计
- 不使用 Inter 字体
```



#### 工作区设置



创建 `.vscode/settings.json`（Cursor 会继承）：

```
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "tailwindCSS.experimental.classRegex": [
    ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"],
    ["cx\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"],
    ["cn\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"],
    ["tv\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"]
  ],
  "emmet.includeLanguages": {
    "typescript": "typescriptreact",
    "javascript": "javascriptreact"
  }
}
```



### VS Code 配置



#### 推荐扩展



1. **TypeScript Hero** - TypeScript 导入管理
2. **Auto Rename Tag** - 自动重命名 HTML/JSX 标签
3. **Bracket Pair Colorizer 2** - 括号配对高亮
4. **Color Highlight** - 颜色值高亮
5. **Indenticator** - 缩进指示器
6. **Material Icon Theme** - 文件图标主题

#### 工作区设置



在 `.vscode/settings.json` 中配置：

```
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "typescript.suggest.autoImports": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "tailwindCSS.includeLanguages": {
    "typescript": "typescript",
    "typescriptreact": "typescriptreact"
  },
  "tailwindCSS.experimental.classRegex": [
    ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"],
    ["cx\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"],
    ["cn\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"],
    ["tv\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"]
  ],
  "emmet.includeLanguages": {
    "typescript": "typescriptreact",
    "javascript": "javascriptreact"
  },
  "files.associations": {
    "*.css": "tailwindcss"
  },
  "css.validate": false,
  "less.validate": false,
  "scss.validate": false
}
```



#### 推荐主题



- **GitHub Dark** - 清晰易读
- **Material Theme** - 现代化设计
- **One Dark Pro** - 受欢迎的深色主题

### Claude Desktop 配置



#### MCP (Model Context Protocol) 服务器配置



在 Claude Desktop 中配置 MCP 服务器以增强 Web3 开发能力。

创建 `claude_desktop_config.json`：

```
{
  "mcpServers": {
    "web3-dev": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-everything", "--port", "3001"],
      "env": {
        "NODE_ENV": "development"
      }
    },
    "blockchain-explorer": {
      "command": "python3",
      "args": ["-m", "mcp_server.blockchain", "--config", "./mcp-blockchain-config.json"],
      "cwd": "/path/to/your/project"
    }
  }
}
```



#### 项目特定的 Claude 配置



在项目根目录创建 `.claude-config.json`：

```
{
  "project": {
    "name": "Web3 Artifacts Builder",
    "type": "react-web3-app",
    "techStack": [
      "React 18",
      "TypeScript",
      "Vite",
      "Tailwind CSS",
      "shadcn/ui",
      "@reown/appkit",
      "viem",
      "zustand",
      "react-i18next"
    ],
    "codingGuidelines": {
      "typescript": "strict",
      "styling": "tailwind-utility-first",
      "componentStructure": "functional-hooks",
      "stateManagement": "zustand-slices",
      "web3Integration": "appkit-viem"
    },
    "designConstraints": {
      "avoidCenteredLayouts": true,
      "avoidPurpleGradients": true,
      "avoidUniformRoundedCorners": true,
      "avoidInterFont": true
    },
    "commitConvention": "conventional-commits"
  },
  "ai": {
    "model": "claude-3-5-sonnet-20241022",
    "temperature": 0.7,
    "maxTokens": 4096
  },
  "development": {
    "autoFixLinting": true,
    "autoFormat": true,
    "runTestsOnSave": false,
    "suggestWeb3Optimizations": true
  }
}
```



#### Claude 提示词模板



创建 `.claude-prompts.md` 文件以定义常用任务：

```
# Web3 Artifacts Builder - Claude 提示词

## 创建新组件
"创建一个名为 {ComponentName} 的 React 组件，使用 TypeScript 和 Tailwind CSS。组件应该：{功能描述}。确保遵循项目的设计指南，避免过度居中布局和紫色渐变。"

## 添加 Web3 功能
"为 {现有组件} 添加 Web3 功能：{功能描述}。使用 @reown/appkit 进行钱包连接，使用 viem 进行区块链交互。确保正确处理异步操作和错误状态。"

## 国际化支持
"为 {组件/页面} 添加国际化支持。创建相应的翻译键，并使用 react-i18next 的 useTranslation hook。支持中英文显示。"

## 状态管理
"使用 zustand 为 {功能} 创建状态管理。创建适当的状态切片，并提供必要的 actions 和 selectors。"

## 样式优化
"为 {组件} 优化 Tailwind CSS 样式。使用 shadcn/ui 组件库，确保响应式设计，并遵循项目的设计原则。"
```



## 开发最佳实践



### 组件开发



- 使用 shadcn/ui 组件库构建一致的 UI
- 利用 TypeScript 获得类型安全
- 遵循组件化开发模式

### Web3 集成



- 使用 @reown/appkit 处理钱包连接
- 利用 viem 进行区块链交互
- 妥善处理网络切换和错误状态

### 状态管理



- 将 Web3 相关状态存储在 zustand store 中
- 使用分离的状态切片管理不同功能模块
- 利用 DevTools 进行调试

### 国际化



- 为所有用户可见文本添加翻译键
- 支持动态内容的多语言显示
- 利用 Trans 组件处理复杂翻译场景

## 故障排除



### 常见问题



1. **钱包连接失败**
   - 检查 Reown 项目 ID 是否正确配置
   - 确认浏览器支持 Web3 钱包
   - 检查网络连接状态
2. **构建失败**
   - 确保 Node.js 版本 >= 18
   - 检查依赖是否完整安装
   - 查看构建日志中的具体错误信息
3. **样式问题**
   - 确认 Tailwind CSS 配置正确
   - 检查 shadcn/ui 组件是否正确导入
   - 验证 CSS 类名是否正确应用

## 许可证



完整条款请查看 [LICENSE.txt](https://github.com/gengbingbing/web3-artifacts-builder-skill/blob/main/LICENSE.txt)

## 相关链接



- [shadcn/ui 组件文档](https://ui.shadcn.com/docs/components)
- [@reown/appkit 文档](https://docs.reown.com/appkit/overview)
- [viem 文档](https://viem.sh/docs/getting-started)
- [react-i18next 指南](https://react.i18next.com/getting-started)
- [zustand 演示](https://zustand-demo.pmnd.rs/) 