# MATH · 数学笔记

一本用 LaTeX 写成的数学笔记，`ctexbook` 中文排版，从**几何学**讲到**概率论**。

写法上不追求"公理—定理—证明"的教科书顺序，而是尽量回答**"为什么会有这个东西"**：先讲清一个概念是被什么问题逼出来的，再落到公式与证明。每章都有大量配图与手算例子，很多是从物理、竞赛题里长出来的动机。

## 编译

需要 **LuaLaTeX**（TeX Live 或 MiKTeX 完整安装均可）。

```bash
latexmk -lualatex -synctex=1 main.tex
```

不用 `latexmk` 的话，手动跑两遍以生成目录与交叉引用：

```bash
lualatex main.tex
lualatex main.tex
```

产物为 `main.pdf`。`main.tex` 首行有 `% !TEX program = lualatex`，TeXstudio / VS Code (LaTeX Workshop) 会直接识别编译器。

**依赖宏包**：`ctex`、`amsmath`、`amssymb`、`amsthm`、`graphicx`、`hyperref`、`booktabs`、`array`、`tikz`（含 `tikz-cd`、`arrows.meta`、`positioning`、`calc` 库）、`multicol`、`wrapfig`、`float`、`subcaption`、`needspace`、`xcolor`。

## 内容结构

| 章 | 节 |
|---|---|
| **第一章 几何学** | 1.1 向量运算 · 1.2 三维空间中的方程 · 1.3 基向量张成平面与曲面 · 1.4 统一思想：n 维体的边界包裹出 n+1 维体的内部 |
| **第二章 微积分** | 2.1 极限 · 2.2 微分 · 2.3 积分 · 2.4 无穷级数 · 2.5 线性微分方程 · 2.6 多元函数微分 · 2.7 多元函数积分 |
| **第三章 线性代数** | 3.1 方程组 · 3.2 矩阵 · 3.3 向量和向量空间 · 3.4 行列式 · 3.5 特征值 · 3.6 正定矩阵 · 3.7 希尔伯特空间 |
| **第四章 群论** | 4.1 群的样貌 · 4.2 群的映射（同态 / 同构 / 自同构） |
| **第五章 概率论** | 5.1 基本知识 · 5.2 几种定理（大数定律 / 中心极限 / 特征函数） · 5.3 概率模型（泊松过程等） |

第一章 1.4 节那条"统一思想"是全书的引子——用同一套"边界包裹内部"的视角串起曲线积分、曲面积分与后面的格林公式、高斯定理。

## 目录结构

```
main.tex        全文（含导言区与全部章节）
main.pdf        编译成品
*.png           插图，由 main.tex 里的 \includegraphics 按文件名引用
```

## 说明

- 所有插图直接以文件名引用，与 `main.tex` 同级；改动插图不会自动被 LaTeX 感知，必要时先删旧的 `.aux` 再编。
- 仓库**不含** LaTeX 中间产物（`.aux` / `.log` / `.out` / `.toc` / `.fls` / `.fdb_latexmk` / `.synctex.gz`），它们由编译重新生成。
- 若需要点击 PDF 跳回源码，编译时保留 `-synctex=1`，用支持 SyncTeX 的阅读器打开 `main.pdf` 即可。
- 纯黑白排版：正文与公式为黑，页眉页脚与提示性文字为灰，无彩色。

## 许可

个人学习笔记，暂未指定开源许可证（默认保留所有权利）。如需引用或转载，请注明出处。
