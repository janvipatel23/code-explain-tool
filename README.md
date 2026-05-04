# 🧠 CodeSplain — AI Code Explanation Tool

**CodeSplain** is a modern AI-powered web application that explains code snippets in plain English. Paste any code, and the tool breaks it down into clear, human-readable explanations. Built with **React 19**, **Vite 5**, and **Tailwind CSS 4** — a fast, lightweight, fully client-side SPA with zero backend infrastructure required.

---

## ✨ Features

- **Instant Code Explanation** — Paste code in any language and get a clear, structured AI-generated explanation.
- **Multi-Language Support** — Works with Python, JavaScript, Java, SQL, TypeScript, and more.
- **Error Boundary Protection** — Powered by `react-error-boundary` for graceful handling of unexpected UI errors.
- **Fast HMR Development** — Vite 5 delivers near-instant hot module replacement during development.
- **Utility-First Styling** — Tailwind CSS 4 with PostCSS for a clean, responsive UI.
- **Linting & Code Quality** — ESLint configured with React, React Hooks, and React Refresh plugins.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│               Browser (SPA — no backend)            │
│                                                     │
│  ┌─────────────────────────────────────────────┐   │
│  │              React 19 App                   │   │
│  │                                             │   │
│  │  ┌──────────────────────────────────────┐  │   │
│  │  │  ErrorBoundary (react-error-boundary) │  │   │
│  │  │                                      │  │   │
│  │  │  Code Input Area                     │  │   │
│  │  │       │                              │  │   │
│  │  │       ▼                              │  │   │
│  │  │  AI API Call (Anthropic / OpenAI)    │  │   │
│  │  │       │                              │  │   │
│  │  │       ▼                              │  │   │
│  │  │  Explanation Output Panel            │  │   │
│  │  └──────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  Bundled by Vite 5 · Styled with Tailwind CSS 4    │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology | Version | Purpose |
|---|---|---|---|
| **Language** | JavaScript (JSX) | ES Modules | Core application language |
| **UI Framework** | React | 19.2.1 | Component-based SPA |
| **Build Tool** | Vite | 5.2.0 | Dev server, HMR, production bundler |
| **Styling** | Tailwind CSS | 4.0.0 | Utility-first CSS framework |
| **CSS Processing** | PostCSS + `@tailwindcss/postcss` | 4.0.0 | Tailwind build pipeline |
| **Error Handling** | react-error-boundary | 4.0.13 | Graceful UI error recovery |
| **React Plugin** | @vitejs/plugin-react | 4.2.1 | JSX transform + Fast Refresh via Vite |
| **Linting** | ESLint 8 | 8.57.0 | Code quality enforcement |
| **ESLint Plugins** | eslint-plugin-react, react-hooks, react-refresh | — | React-specific lint rules |

---

## 📁 Project Structure

```
code-explain-tool/
├── index.html              # App entry point — title: "CodeSplain", mounts /src/main.jsx
├── package.json            # Dependencies, scripts (dev / build / lint / preview)
├── postcss.config.js       # PostCSS config for Tailwind CSS 4
├── .gitignore
├── LICENSE                 # Apache-2.0
├── README.md
│
├── public/                 # Static assets (favicon, icons)
│   └── vite.svg
│
└── src/                    # React application source
    ├── main.jsx            # React DOM root render
    ├── App.jsx             # Root component — layout and routing
    ├── index.css           # Tailwind base styles
    └── components/         # Reusable UI components
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### 1. Clone the Repository

```bash
git clone https://github.com/janvipatel23/code-explain-tool.git
cd code-explain-tool
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure API Key

Create a `.env` file in the project root and add your AI provider API key:

```env
VITE_API_KEY=your_api_key_here
```

> **Note:** Vite exposes only variables prefixed with `VITE_` to the browser. Never commit your `.env` file — it is already listed in `.gitignore`.

### 4. Start the Development Server

```bash
npm run dev
```

Open your browser at `http://localhost:5173`.

---

## 📜 Available Scripts

| Script | Command | Description |
|---|---|---|
| **dev** | `npm run dev` | Start Vite dev server with HMR |
| **build** | `npm run build` | Production build to `dist/` |
| **preview** | `npm run preview` | Preview the production build locally |
| **lint** | `npm run lint` | Run ESLint across all `.js` and `.jsx` files |

---

## 🔄 How It Works

```
User pastes code into the input area
              │
              ▼
Code is sent to AI API with an explanation prompt
              │
              ▼
AI returns a structured plain-English breakdown:
  ├── What the code does overall
  ├── Step-by-step line/block explanation
  └── Key concepts or patterns used
              │
              ▼
Explanation rendered in the output panel
(ErrorBoundary wraps the entire flow for safety)
```

---

## ⚙️ Configuration Reference

| Parameter | Value | Description |
|---|---|---|
| App title | `CodeSplain` | Set in `index.html` |
| Entry point | `/src/main.jsx` | React DOM root |
| Dev server port | `5173` (default) | Vite default port |
| Build output | `dist/` | Production bundle directory |
| Module type | `"module"` | ES Modules throughout |
| React version | `19.2.1` | Latest React with concurrent features |
| Tailwind version | `4.0.0` | CSS-first configuration (no `tailwind.config.js` needed) |

---

## 📦 Dependencies

### Runtime
```json
"react": "^19.2.1",
"react-dom": "^19.2.1",
"react-error-boundary": "^4.0.13"
```

### Dev / Build
```json
"vite": "^5.2.0",
"@vitejs/plugin-react": "^4.2.1",
"tailwindcss": "^4.0.0",
"@tailwindcss/postcss": "^4.0.0",
"postcss": "^8.4.38",
"eslint": "^8.57.0",
"eslint-plugin-react": "^7.34.1",
"eslint-plugin-react-hooks": "^4.6.0",
"eslint-plugin-react-refresh": "^0.4.6"
```

Install all at once:
```bash
npm install
```

---

## 🏗️ Building for Production

```bash
npm run build
```

Output is generated in the `dist/` directory. Deploy to any static hosting platform:

```bash
# Vercel
vercel --prod

# Netlify
netlify deploy --prod --dir=dist

# GitHub Pages
# Push dist/ contents to gh-pages branch
```

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome! Feel free to open a pull request or issue on [GitHub](https://github.com/janvipatel23/code-explain-tool).

---

## 📄 License

This project is licensed under the **Apache-2.0 License**. See the [LICENSE](./LICENSE) file for details.