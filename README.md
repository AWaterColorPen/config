# config

[![Go](https://github.com/AWaterColorPen/config/actions/workflows/go.yml/badge.svg)](https://github.com/AWaterColorPen/config/actions/workflows/go.yml)

## Introduction

Config is a light pluggable dynamic config package without useless dependencies.
Base on forked from [github.com/go-micro/go-micro/config](https://github.com/go-micro/go-micro/tree/master/config).

## Features

- dynamic loading
- pluggable sources
- mergeable config
- observe changes
- sane defaults

## Getting Started

### Load and get

load config from `env`, `flag` and `file`.

```golang
if err := config.Load(env.NewSource()); err != nil {
    return err
}

if err := config.Load(flag.NewSource(flag.IncludeUnset(true))); err != nil {
    return err
}

configFile := "config_file.json"
if err := config.Load(file.NewSource(file.WithPath(configFile))); err != nil {
    return err
}
```

get config to struct

```golang
func Scan(v any, path ...string) error {
    return config.Get(path...).Scan(v)
}
```

## License

See the [License File](./LICENSE).
