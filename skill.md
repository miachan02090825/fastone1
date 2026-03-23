| name                  | description                                                  | license                       |
| --------------------- | ------------------------------------------------------------ | ----------------------------- |
| web-artifacts-builder | Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui) with Web3 support. Includes EVM chain configuration, wallet connections (@reown/appkit), internationalization (react-i18next), state management (zustand), and utility hooks (react-use). Use for complex artifacts requiring state management, routing, Web3 integration, or shadcn/ui components - not for simple single-file HTML/JSX artifacts. | Complete terms in LICENSE.txt |

# Web Artifacts Builder



To build powerful frontend claude.ai artifacts with Web3 capabilities, follow these steps:

1. Initialize the frontend repo using `scripts/init-artifact.sh`
2. Develop your artifact by editing the generated code
3. Bundle all code into a single HTML file using `scripts/bundle-artifact.sh`
4. Display artifact to user
5. (Optional) Test the artifact

**Stack**: React 18 + TypeScript + Vite + Parcel (bundling) + Tailwind CSS + shadcn/ui + Web3 (@reown/appkit, viem) + i18n (react-i18next) + State Management (zustand) + Utility Hooks (react-use)

## Design & Style Guidelines



VERY IMPORTANT: To avoid what is often referred to as "AI slop", avoid using excessive centered layouts, purple gradients, uniform rounded corners, and Inter font.

## Web3 & Development Features



### Web3 Integration



- **@reown/appkit**: Modern wallet connection modal with support for MetaMask, WalletConnect, Coinbase Wallet, and more
- **viem**: TypeScript interface for Ethereum with full EVM chain support
- Pre-configured EVM chains: Ethereum Mainnet, Polygon, BSC, Arbitrum, Optimism, Base
- Built-in wallet connection hooks and utilities

### Internationalization



- **react-i18next**: Complete i18n solution with TypeScript support
- Pre-configured English and Chinese locales
- Type-safe translation keys with auto-completion
- React component integration with `<Trans>` and `useTranslation` hook

### State Management



- **zustand**: Lightweight, fast state management with TypeScript
- Pre-configured store structure with Web3 and UI state slices
- DevTools integration for debugging
- Middleware support for persistence and logging

### Utility Hooks



- **react-use**: Collection of essential React hooks
- Common patterns: useLocalStorage, useAsync, useToggle, useInterval, etc.
- Performance optimizations and lifecycle hooks

### Development Tools



- **Husky**: Git hooks for code quality enforcement
- **lint-staged**: Run linters only on staged files for faster commits
- **Commitlint**: Enforce conventional commit message standards
- **GitHub Actions**: Automated CI/CD pipelines with testing and building
- **Dependabot**: Automated dependency updates with security alerts

## Quick Start



### Step 1: Initialize Project



Run the initialization script to create a new React project:

```
bash scripts/init-artifact.sh <project-name>
cd <project-name>
```



This creates a fully configured project with:

- ✅ React + TypeScript (via Vite)
- ✅ Tailwind CSS 3.4.1 with shadcn/ui theming system
- ✅ Path aliases (`@/`) configured
- ✅ 40+ shadcn/ui components pre-installed
- ✅ All Radix UI dependencies included
- ✅ Web3 Integration (@reown/appkit, viem) with EVM chain support
- ✅ Internationalization (react-i18next) with English/Chinese locales
- ✅ State Management (zustand) with TypeScript support
- ✅ Utility Hooks (react-use) for common React patterns
- ✅ Development Tools (Husky, lint-staged, Commitlint)
- ✅ GitHub Actions CI/CD workflows with testing and releases
- ✅ Dependabot automated dependency updates
- ✅ Parcel configured for bundling (via .parcelrc)
- ✅ Node 18+ compatibility (auto-detects and pins Vite version)

### Step 2: Develop Your Artifact



To build the artifact, edit the generated files. See **Common Development Tasks** below for guidance.

#### Development Workflow:



**Git Hooks & Code Quality:**

```
# Pre-commit hooks will automatically run:
npx lint-staged  # Runs ESLint and Prettier on staged files

# Commit messages must follow conventional format:
git commit -m "feat: add wallet connection feature"
git commit -m "fix: resolve balance display bug"
git commit -m "docs: update README with new features"

# Available commit types: build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test, wip
```



#### Web3 Development Examples:



```
// Wallet connection
import { useAppKit } from '@reown/appkit/react'
import { useAppKitAccount } from '@reown/appkit/react'

function WalletConnect() {
  const { open } = useAppKit()
  const { address, isConnected } = useAppKitAccount()

  return (
    <button onClick={() => open()}>
      {isConnected ? `Connected: ${address}` : 'Connect Wallet'}
    </button>
  )
}

// Internationalization
import { useTranslation } from 'react-i18next'

function MyComponent() {
  const { t } = useTranslation()

  return <h1>{t('welcome.title')}</h1>
}

// State management with zustand
import { useStore } from '@/store'

function Counter() {
  const { count, increment } = useStore()

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  )
}
```



### Step 3: Bundle to Single HTML File



To bundle the React Web3 app into a single HTML artifact:

```
bash scripts/bundle-artifact.sh
```



This creates `bundle.html` - a self-contained artifact with all JavaScript, CSS, and Web3 dependencies inlined. This file can be directly shared in Claude conversations as an artifact.

**Requirements**:

- Your project must have an `index.html` in the root directory
- Recommended: Configure `.env` with your Reown project ID for Web3 features

**What the script does**:

- ✅ Validates environment configuration for Web3
- ✅ Installs optimized bundling dependencies (Parcel 2.12.0)
- ✅ Creates Web3-optimized Parcel configuration
- ✅ Builds with tree-shaking and minification
- ✅ Adds Content Security Policy for wallet connections
- ✅ Inlines all assets with compression metrics
- ✅ Validates final bundle integrity
- ✅ Shows build time and compression statistics

### Step 4: Share Artifact with User



Finally, share the bundled HTML file in conversation with the user so they can view it as an artifact.

### Step 5: Testing/Visualizing the Artifact (Optional)



Note: This is a completely optional step. Only perform if necessary or requested.

To test/visualize the artifact, use available tools (including other Skills or built-in tools like Playwright or Puppeteer). In general, avoid testing the artifact upfront as it adds latency between the request and when the finished artifact can be seen. Test later, after presenting the artifact, if requested or if issues arise.

## Reference



- **shadcn/ui components**: https://ui.shadcn.com/docs/components
- **@reown/appkit**: https://docs.reown.com/appkit/overview
- **viem**: https://viem.sh/docs/getting-started
- **react-i18next**: https://react.i18next.com/getting-started
- **zustand**: https://zustand-demo.pmnd.rs/
- **react-use**: https://github.com/streamich/react-use
- **Husky**: https://typicode.github.io/husky/
- **lint-staged**: https://github.com/okonet/lint-staged
- **Commitlint**: https://commitlint.js.org/
- **GitHub Actions**: https://docs.github.com/en/actions

### Pre-configured Chains



- Ethereum Mainnet (1)
- Polygon (137)
- BSC (56)
- Arbitrum One (42161)
- Optimism (10)
- Base (8453)