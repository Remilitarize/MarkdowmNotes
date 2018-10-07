[toc]

> 不推荐 CTeX。

## 安装 Tex Live

1. [官网地址](http://tug.org/texlive/)
2. 下载好后，使用虚拟光驱或解压，双击光盘根目录下的 `install-tl-advanced.bat` 进行安装。
3. 注意安装路径最好是纯英文（空格也不要有）。
4. 如果习惯使用 vscode 进行编写 LaTeX，下面将会给出 vscode 的具体配置。
5. 如果不适用 vscode，则可以通过开始菜单中 `Tex Live 2017` 文件夹下 `TeXworks Editor` 进行编写。

### vscode 配置

1. 安装好 vscode 和 TexLive。
2. 进入 vscode，安装插件 `LaTeX Workshop`。
3. 配置好 PATH 环境变量，`%TexLive目录%\2017\bin\win32`。
4. 按下 `ctrl + ,`，进入 User Setting，在右侧用户设置区将下面代码复制粘贴。
5. 创建一个纯英文（没有空格）的工作目录，新建一个以 `.tex` 为后缀的文件。
6. 文件编写完后，`ctrl + alt + b` 或鼠标右键菜单中选择 `Build LaTeX project` 编译，`ctrl + alt + v` 或点击右上角 `View LaTeX PDF file` 按钮查看。

```json
"latex-workshop.latex.recipes": [
        {
          "name": "xelatex",
          "tools": [
            "xelatex"
          ]
        },
        {
          "name": "xelatex -> bibtex -> xelatex*2",
          "tools": [
            "xelatex",
            "bibtex",
            "xelatex",
            "xelatex"
          ]
        }
      ],
      "latex-workshop.latex.tools": [
        {
          "name": "latexmk",
          "command": "latexmk",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-pdf",
            "%DOC%"
          ]
        },
        {
          "name": "xelatex",
          "command": "xelatex",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
          ]
        },
        {
          "name": "bibtex",
          "command": "bibtex",
          "args": [
            "%DOCFILE%"
          ]
        }
      ],
    "latex-preview.command": "xelatex",
    "latex-workshop.latex.clean.enabled": true, 
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk",
        "*.gz"
    ]
```

## TeX Live 开始菜单介绍

- `TeXworks editor`
    - 一个 TeX 文件编辑器。
- `DVIOUT DVI viewer`
    - 一个 DVI 文件预览器，很少用到。
- `PS_View`
    - PostScript 文件查看工具，也可以查看 PDF 文件，但效果不如 `Adobe Reader`。
    - `.ps` 和 `.eps` 文件与之关联。
- `TeX Live command-line`
    - 打开 Windows 的命令提示符。
    - 设置好必要的环境变量后，可以在其中使用命令行编译处理 TeX 文档。
- `TeX Live documentation`
    - TeX Live 中所有 PDF 或 HTML 格式的文档列表（相当于 API）。
- `TeXdoc GUI`
    - 图形界面的文档列表（但数量较少）。
- `TeX Live Manager`
    - 图形化管理工具。
    - 可以使用命令 `tlmgr` 启动。


