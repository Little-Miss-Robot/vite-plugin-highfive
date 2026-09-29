# @littlemissrobot/vite-plugin-highfive

A tiny Vite plugin that enables decorator support for [Highfive](https://github.com/Little-Miss-Robot/highfive) using Babel and Rolldown.

## Installation

```bash
npm install @littlemissrobot/vite-plugin-highfive
```

## Usage

Add `highfive()` to your Vite configuration:

```ts
import { defineConfig } from 'vite'
import highfive from '@littlemissrobot/vite-plugin-highfive'

export default defineConfig({
  plugins: [
    highfive(),
  ],
})
```

That's it.

You can now use decorators required by Highfive in your Vite application.

## What does it do?

Vite 8 uses Rolldown internally. Highfive relies on modern JavaScript decorators, which require an additional transform step.

This plugin configures `@rolldown/plugin-babel` with Babel's decorators transform using the `2023-11` decorators proposal:

```ts
babel({
  presets: [
    decoratorPreset({
      version: '2023-11',
    }),
  ],
})
```

The Babel transform is only applied to source code containing `@`, avoiding unnecessary transforms for files that don't use decorators.

## Requirements

- Vite 8+
- Node.js version supported by Vite 8

## License

ISC