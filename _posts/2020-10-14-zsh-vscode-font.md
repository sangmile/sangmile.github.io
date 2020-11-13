---
layout: post
title: "ZSH Font Setting in VSCODE"
date: 2020-10-13 00:52:00 +0400
categories: env
---

VSCode에서 zsh font 깨짐 현상
-------------------

> VS Code에서 zsh을 실행했을 때 font가 깨지는 현상 발생.

1. font 확인   
`zsh`을 설치하면서 함께 설치한 font 확인.

    ```bash
    apt install fonts-powerline
    ```

2. VS Code 설정   
VS Code에 setting.json 파일에서 **editor.fontFamily**에 설치한 폰트인 `PowerlineSymbols` 추가

    ```json
    "editor.fontFamily": "'PowerlineSymbols', 'Droid Sans Mono', 'monospace', monospace"
    ```

