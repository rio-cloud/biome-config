# biome-config

A place for all our biome configs - with the hope that it's only going to be one, actually

## 🐶 Disclaimers

Right now, only the [frontend](configs/frontend.json) config exists.

At the time of writing, this config is working with [biome](https://www.npmjs.com/package/@biomejs/biome)
**version 2.3.5** and most likely above.

⚠️ There have been some fluctuations regarding config structure in the past, though - so if you're running a newer biome
version and experience weird behaviour, please [get in touch](https://github.com/rio-cloud/biome-config/issues). 

## Installation

Add this npm package to your project's `devDependencies:

```shell
npm install --save-dev @rio-cloud/biome-config
```

Now, your minimal `biome.json` could look like this:

```json
{
    "$schema": "./node_modules/@biomejs/biome/configuration_schema.json",
    "extends": ["@rio-cloud/biome-config/frontend.json"],
    "files": {
        "includes": [
            "**",
            "!.*",
            "!**/node_modules"
        ]
    }
}
```

**Make sure to tune your `files.includes` to match your project structure!** (see
[the biome docs](https://biomejs.dev/guides/configure-biome/#include-files-via-configuration) for reference).
