+++
author = "Przeblysk"
title = "git commit husky npx not found"
date = "2022-1-5"
description = "husky在第三方git gui中不能正确找到path路径的问题"
categories = [
    "Problem"
]
tags = [
    "git",
    "husky"
]

image = "animal-6889575_1920.jpg"

+++

基本上的表现为 xx command not found 例如 npx command not found. yarn command not found.

**解决办法**

在用户根目录新建.huskyrc 将环境写入其中，例如 nvm 安装的 node 环境

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

export PATH=$HOME/.nvm/versions/node/v16.13.0/bin:$PATH # Add yarn to path
```
