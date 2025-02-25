# React + Vite + Tailwind CSS + shadcn/ui Project Initialization

[![react][react-badge]][react-url]
[![vite][vite-badge]][vite-url]
[![tailwind][tailwind-badge]][tailwind-url]
[![shadcn][shadcn-badge]][shadcn-url]
[![linkedIn][linkedin-badge]][linkedin-url]

This tutorial guides you through the initialization of the following stack:
- [React 19](https://react.dev/)
- [Vite](https://vite.dev/)
- [Tailwind CSS 4](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)

## Table of Contents
1. [Project Creation & Initialization](#1-project-creation--initialization)
   1. [Project Creation](#1-project-creation)
   2. [Project Initialization](#2-project-initialization)
2. [Tailwind CSS Installation & Configuration](#2-tailwind-css-installation--configuration)
   1. [Tailwind CSS Installation](#1-tailwind-css-installation)
   2. [Tailwind CSS & Vite Configuration](#2-tailwind-css--vite-configuration)
   3. [Import Tailwind CSS](#3-import-tailwind-css)
   4. [Remove App.css](#4-remove-appcss)
3. [Path Aliases Configuration](#3-path-aliases-configuration)
   1. [tsconfig.json Configuration](#1-tsconfigjson-configuration)
   2. [tsconfig.app.json Configuration](#2-tsconfigappjson-configuration)
4. [@types/node Installation & Configuration](#4-typesnode-installation--configuration)
   1. [@types/node Installation](#1-typesnode-installation)
   2. [Resolve alias](#2-resolve-alias)
5. [Shadcn/ui Installation & Configuration](#5-shadcnui-installation--configuration)
   1. [Shadcn/ui Installation](#1-shadcnui-installation)
   2. [Shadcn/ui usage](#2-shadcnui-usage)
6. [Possible Errors](#6-possible-errors)
   1. [Extra Semicolon](#1-extra-semicolon)
   2. [Dark Mode](#2-dark-mode)
   3. [Plugins](#3-plugins)

## 1. Project Creation & Initialization

### 1. Project Creation

Create a new project with `React 19` using `Vite` and `pnpm`.

```
pnpm create vite --template=react-ts
```

### 2. Project Initialization

Initialize project and dependencies with the following commands:

```
cd [PROJECT_FOLDER]
pnpm install
```

## 2. Tailwind CSS Installation & Configuration

### 1. Tailwind CSS Installation

Install `tailwindcss` and `@tailwindcss/vite` using `pnpm`.

```
pnpm install tailwindcss @tailwindcss/vite
```

### 2. Tailwind CSS & Vite Configuration

Add the `@tailwindcss/vite` plugin to your Vite configuration `vite.config.ts`.

```
import { defineConfig } from 'vite';

import tailwindcss from '@tailwindcss/vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [
    react(),
    tailwindcss()
  ]
})
```

### 3. Import Tailwind CSS

Replace your `index.css` file with the following code:

```
@import "tailwindcss";
```

The application style will be generated during the `shadcn/ui` initialization.

### 4. Remove App.css

This `App.css` file is not needed for this tutorial, but you can keep it if desired.

## 3. Path Aliases Configuration

### 1. tsconfig.json Configuration

Add the following path aliases to `tsconfig.json`:

```
{
  "files": [],
  "references": [
    {
      "path": "./tsconfig.app.json"
    },
    {
      "path": "./tsconfig.node.json"
    }
  ],
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": [
        "./src/*"
      ]
    }
  }
}
```

### 2. tsconfig.app.json Configuration

Add the following path aliases to `tsconfig.app.json`:

```
{
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.app.tsbuildinfo",
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedSideEffectImports": true,

    /* Path Aliases */
    "baseUrl": ".",
    "paths": {
      "@/*": [
        "./src/*"
      ]
    }
  },
  "include": ["src"]
}
```

## 4. @types/node Installation & Configuration

### 1. @types/node Installation

Install `@types/node` via `pnpm`.

```
pnpm add -D @types/node
```

### 2. Resolve alias

Add the resolve alias configuration to `vite.config.ts`.

```
import path from 'path';
import { defineConfig } from 'vite';

import tailwindcss from '@tailwindcss/vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [
    react(),
    tailwindcss()
  ],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src")
    }
  }
})
```

## 5. Shadcn/ui Installation & Configuration

### 1. Shadcn/ui Installation

Install `shadcn/ui`, this will create your `components.json` and set up your CSS variables in `index.css`.

```
pnpm dlx shadcn@canary init
```

### 2. Shadcn/ui usage

You should now be able to add `shadcn/ui` components.

```
pnpm dlx shadcn@canary add button
```

## 6. Possible Errors

### 1. Extra Semicolon

When initializing `shadcn/ui`, an extra semicolon may be added to a CSS class in `index.css`. This can prevent the application from starting and can be fixed by removing the extra semicolon:

```
--radius: 0.625rem;;
```

### 2. Dark Mode

In `Tailwind CSS 4`, dark mode is handled using the built-in dark mode configuration. You may need to remove the following code from your CSS file:

```
@custom-variant dark (&:is(.dark *));
```

### 3. Plugins

In `Tailwind CSS 4`, the `@option` plugin is no longer used and has been replaced by `@import`.

```
@plugin "tailwindcss-animate";
```

```
@import "tailwindcss-animate";
```

<!-- MARKDOWN LINKS & IMAGES -->
[react-badge]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[react-url]: https://react.dev/
[vite-badge]: https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E
[vite-url]: https://vite.dev/
[tailwind-badge]: https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white
[tailwind-url]: https://tailwindcss.com/
[shadcn-badge]: https://img.shields.io/badge/shadcn%2Fui-000000?style=for-the-badge&logo=shadcnui&logoColor=white
[shadcn-url]: https://ui.shadcn.com/
[linkedin-badge]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/antoine-regnier-1bba96112/