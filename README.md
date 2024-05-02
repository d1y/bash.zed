# Bash for Zed

Tree Sitter: https://github.com/tree-sitter/tree-sitter-bash

Language Server: https://github.com/bash-lsp/bash-language-server

![image.png](https://s2.loli.net/2024/03/30/ISb1wqOCYaZtLyc.png)

# Shellcheck

The [bash-language-server](https://github.com/bash-lsp/bash-language-server) support shellcheck.
But you need to [install it manually](https://github.com/koalaman/shellcheck#installing)

```bash
brew install shellcheck
```

# Shfmt

The https://github.com/bash-lsp/bash-language-server/pull/1136 PR add [shfmt](https://github.com/mvdan/sh), Waiting for merge you can use format :)

```bash
go install mvdan.cc/sh/v3/cmd/shfmt@latest
```

Or configure it manually

```json
{
  "language_overrides": {
    "Shell Script": {
      "formatter": {
        "external": {
          "command": "shfmt", // Not work? try use full-path: /Users/d1y/go/bin/shfmt
          "arguments": ["{buffer_path}"]
        }
      }
    }
  }
}
```
