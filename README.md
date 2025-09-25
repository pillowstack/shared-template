# Shared Template

A minimal TypeScript + SCSS shared template library with complete development tooling:
ESLint, Prettier, Husky + lint-staged, and CI/CD via GitHub Actions.

---

## 📦 What's Included

- **TypeScript Types**: Shared type definitions for consistent data structures
- **SCSS Styles**: iOS/iPadOS-inspired design system (typography, colors, utilities)
- **Development Tools**: Preconfigured linting, formatting, and Git hooks
- **CI/CD**: Automated build, lint, test, and publish workflows on GitHub Actions

---

## 🚀 Quick Start

### Requirements

- Node.js **>= 20.0.0**
- npm or yarn
- (Optional) GitHub Personal Access Token for private installation

### Installation

**From Public npm Registry:**

```bash
npm install @pillowstack/shared-template
```

**From GitHub Packages (Private):**

1. Create a GitHub Personal Access Token with `read:packages`.
2. Add to `~/.npmrc` or project `.npmrc`:

```bash
//npm.pkg.github.com/:_authToken=YOUR_GITHUB_TOKEN
@pillowstack:registry=https://npm.pkg.github.com
```

3. Install:

```bash
npm install @pillowstack/shared-template
```

---

## 📖 Usage

### TypeScript Types

```ts
import type {
  Profile,
  Name,
  Bio,
  Settings,
  Theme,
  Language,
  Mode,
} from "@pillowstack/shared-template";

const userProfile: Profile = { name: "John Doe", bio: "Software Developer" };
const appSettings: Settings = { theme: "dark", language: "en" };
const syncMode: Mode = "sync";
```

---

### SCSS Styles

Two ways to consume:

**Method 1: Import Everything**

```scss
@use "@pillowstack/shared-template/styles" as *;
// or
@use "@pillowstack/shared-template/styles/_index" as *;
```

**Method 2: Selective Imports**

```scss
@use "@pillowstack/shared-template/styles/_variables" as vars;
@use "@pillowstack/shared-template/styles/_mixins" as mixins;
@use "@pillowstack/shared-template/styles/type/_medium" as typography;

.my-component {
  font-family: vars.$font-family;
  @include mixins.no-select;
  @extend %type-body;
}
```

**Available Style Modules**

- Core: `_variables.scss`, `_mixins.scss`, `_reset.scss`, `root.scss`
- Colors: light, dark, and high-contrast themes
- Typography: responsive type scales (`_xsmall` → `_xxxlarge`)

**Using CSS Variables**

```css
.my-element {
  background: var(--rgba-background);
  color: var(--rgba-text);
  border-color: var(--rgb-gray-3);
}
```

---

## 🛠️ Development

### Setup

```bash
git clone https://github.com/pillowstack/shared-template.git
cd shared-template
npm ci
npm run prepare
```

### Scripts

| Command             | Description                        |
| ------------------- | ---------------------------------- |
| `npm run lint`      | Check for linting errors           |
| `npm run lint:fix`  | Fix linting errors automatically   |
| `npm run stylelint` | Lint SCSS files                    |
| `npm run format`    | Format with Prettier               |
| `npm run build`     | Emit TypeScript declarations       |
| `npm run clean`     | Remove generated files             |
| `npm run pack`      | Clean + build and pack npm tarball |
| `npm run test*`     | Run unit tests with Vitest         |

---

## 📂 Project Structure

```
shared-template/
├── .codex/           # AI agent config and prompts
├── .github/          # CI/CD workflows and issue templates
├── .husky/           # Git hooks
├── styles/           # SCSS source files
│   ├── colors/      # Theme colors
│   ├── type/        # Typography scales
│   ├── _variables.scss
│   ├── _mixins.scss
│   ├── _reset.scss
│   └── root.scss
├── types/            # TypeScript definitions
│   └── types/       # Source TS files
├── eslint.config.js
├── stylelint.config.js
├── tsconfig.build.json
└── package.json
```

---

## 🚢 Publishing

Automatic publishing on new version tags pushed to `main`:

```bash
npm version patch # or minor, major
git push origin main --follow-tags
```

Manual publish:

```bash
export NODE_AUTH_TOKEN=your_github_token_with_write_packages
npm run build
npm publish
```

---

## 🤝 Contributing

We accept:

- Critical bug fixes
- Security patches
- Minor non-breaking improvements
- Documentation updates

Follow Conventional Commits:

- `feat:` new features
- `fix:` bug fixes
- `docs:` documentation only
- `style:` formatting only
- `refactor:` code restructuring
- `test:` test updates
- `chore:` maintenance tasks

---

## 📄 License

MIT © Pillowstack
See [LICENSE](./LICENSE) for details.

---

## 💬 Support

- **Issues**: [GitHub Issues](https://github.com/pillowstack/shared-template/issues)
- **Discussions**: [Pillowstack](https://github.com/pillowstack/.github/discussions)
- **Security**: See [SECURITY.md](SECURITY.md) for reporting vulnerabilities

## 🙏 Acknowledgments

- Design inspired by Apple HIG
- Built with TypeScript + SCSS
- Maintained by [Pillowstack](https://github.com/pillowstack)

---

## 📈 Changelog

- **v1.0.1** Updated dependencies.
- **v1.0.0** Major release.
