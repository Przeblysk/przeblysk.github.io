+++
author = "Przeblysk"
title = "Unable to resolve your shell environment in a reasonable time. Please review your shell configuration."
date = "2022-1-5"
description = "vscode 启动时运行环境加载时间过长的问题"
categories = [
    "Problem"
]
tags = [
    "vscode",
]

image = "winter-gbf2e41a68_1920.jpg"

+++

问题表现为启动vscode的时候右下角会有一个提示Unable to resolve your shell environment in a reasonable time. Please review your shell configuration.

在GitHub上有同样的issue被提出：[`Unable to resolve your shell environment` notification after VS Code restored during MacOS restart · Issue #113869 · microsoft/vscode (github.com)](https://github.com/microsoft/vscode/issues/113869#issuecomment-780072904)

官网描述地址[Visual Studio Code Frequently Asked Questions](https://code.visualstudio.com/docs/supporting/faq#_resolving-shell-environment-is-slow-error-warning)

我的解决方案是在vscode中不主动加载nvm环境，我的本地配置文件是**.zshrc**，因为我是用的是ohmyzsh。

修改**.zshrc**配置如下

```bash
function load_nvm() {
  export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
  [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
}

# nvm
if [[ "x${TERM_PROGRAM}" = "xvscode" ]]; then 
  echo 'in vscode, nvm not work; use `load-nvm`';
else 
  load_nvm
fi

```

这样就解决啦 :)
