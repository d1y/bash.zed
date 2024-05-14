# Bash for Zed

Tree Sitter: https://github.com/tree-sitter/tree-sitter-bash

Language Server: https://github.com/bash-lsp/bash-language-server

![image.png](https://s2.loli.net/2024/03/30/ISb1wqOCYaZtLyc.png)

# shellcheck

The [bash-language-server](https://github.com/bash-lsp/bash-language-server) support shellcheck.
But you need to [install it manually](https://github.com/koalaman/shellcheck#installing)

```bash
brew install shellcheck
```

# shfmt

lsp support format

> https://github.com/bash-lsp/bash-language-server/pull/1136

```bash
go install mvdan.cc/sh/v3/cmd/shfmt@latest
```

# tldr vs man

`bash-language-server` use `man` to show document 👀

The markdown rendering is completely bad

So, let's just use the documentation provided by tldr (it's really a markdown display!)

github: https://github.com/d1ylab/bash-language-server

npm: https://www.npmjs.com/package/neo-bash-ls

| After      | Before |
| ----------- | ----------- |
| ![image.png](https://s2.loli.net/2024/05/15/WNXcxehtRAf2I9a.png)      | ![image.png](https://s2.loli.net/2024/05/15/IPitmeKo8Awjq25.png)       |

Apply the patch

```diff
diff --git a/src/bash.rs b/src/bash.rs
index d9cdd6b..d8fc8f5 100644
--- a/src/bash.rs
+++ b/src/bash.rs
@@ -1,8 +1,8 @@
 use std::{env, fs};
 use zed_extension_api::{self as zed, Result};

-const SERVER_PATH: &str = "node_modules/bash-language-server/out/cli.js";
-const PACKAGE_NAME: &str = "bash-language-server";
+const SERVER_PATH: &str = "node_modules/neo-bash-ls/out/cli.js";
+const PACKAGE_NAME: &str = "neo-bash-ls";

 struct BashExtension {
     did_find_server: bool,
```