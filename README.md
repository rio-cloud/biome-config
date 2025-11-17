# biome-config

A place for all our biome configs - with the hope that it's only going to be one, actually

## 🐶 Disclaimers

Right now, only the [frontend](frontend.json) config exists, but it should work for non-frontend codebases just as well.

At the time of writing, this config is working with [biome](https://www.npmjs.com/package/@biomejs/biome)
**version 2.3.5** and most likely above.

⚠️ There have been some fluctuations regarding config structure in the past, though - so if you're running a newer biome
version and experience weird behaviour, please [get in touch](https://github.com/rio-cloud/biome-config/issues). 

## 🛠️ Installation

Add this npm package to your project's `devDependencies:

```shell
npm install --save-dev @rio-cloud/biome-config
```

Now, your minimal `biome.json` could look like this:

```json
{
    "$schema": "node_modules/@biomejs/biome/configuration_schema.json",
    "extends": ["@rio-cloud/biome-config/frontend.json"],
    "root": true,
    "files": {
        "includes": [
            "**",
            "!.*",
            "!**/node_modules",
            "src",
            "!dist"
        ]
    }
}
```

**Make sure to tune your `files.includes` to match your project structure!** (see
[the biome docs](https://biomejs.dev/guides/configure-biome/#include-files-via-configuration) for reference).

## 💪 Using it

To make interacting with biome in the terminal easier, you can add some
[npm scripts](https://docs.npmjs.com/cli/v11/using-npm/scripts) to your `package.json`:

```json5
{
  /* ... */
  "scripts": {
    /* ... */
    "format-code": "biome format --write .",
    "lint": "biome lint .",
    "lint-fix": "biome lint --write .",
    "lint-fix-unsafe": "biome lint --write --unsafe .",
  }
  /* ... */
}
```

Depending on your IDE, we also recommend to activate biome and have it fix stuff on save automatically for you. There
is a pretty good [biome extension for intelliJ](https://plugins.jetbrains.com/plugin/22761-biome) that allows these
settings, for example:

![intelliJ biome settings](docs/biome-settings-intellij.png)

## ❤️ Contributing

If you have a biome config that would like to see added here, please double-check if there's not already one that works
for you. The [frontend](frontend.json) config should be sufficient for most (if not all) projects that are using TypeScript. And
remember that you can always overrule or add settings to your local biome config without having to push those settings
"upstream". After all, the configs in this repository are supposed to be a solid baseline for most of our projects - and
hopefully, we can homogenize our code a bit.

If you see a config here and **do want** to change settings because you're sure that change needs to happen for everyone
at RIO, feel free to [open an issue on GitHub](https://github.com/rio-cloud/biome-config/issues) 😎
