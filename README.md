# CUGThesis

面向中国地质大学（武汉）本科毕业论文写作场景的 LaTeX 示例工程与 AI 辅助写作教程。

本项目以 `CUGThesis` LaTeX 模板为基础，整理了一套从 AI 协作写作、Markdown 初稿、LaTeX 模板迁移、BibTeX 文献管理到最终 PDF 编译的完整流程。仓库中的示例论文主题为“AI 辅助本科毕业论文写作全流程方法研究与实践”，可作为学习 Codex 辅助论文写作和 LaTeX 排版的参考。

## 项目内容

```text
.
├── 教程.pdf                         # 完整教程 PDF
└── latex_document/
    ├── Thesis.tex                   # 论文主文件
    ├── CUGThesis.cls                # 中国地质大学（武汉）论文模板类文件
    ├── Bibs/
    │   └── mybib.bib                # BibTeX 参考文献数据库
    ├── Figures/                     # 论文插图
    ├── gbt7714-2005.bst             # 参考文献样式
    ├── simsun.ttc                   # 宋体字体文件
    ├── simhei.ttf                   # 黑体字体文件
    ├── STKAITI.TTF                  # 华文楷体字体文件
    └── build/                       # 编译生成文件
```

## 适合谁使用

- 想用 AI 辅助完成本科毕业论文初稿整理、润色和格式迁移的学生
- 想学习 Codex 如何读写本地论文工程文件的用户
- 想把 Markdown 草稿迁移到 LaTeX 学校模板中的用户
- 想了解 BibTeX、Figures 文件夹和 LaTeX 编译流程的 LaTeX 初学者
- 需要中国地质大学（武汉）本科毕业论文 LaTeX 示例工程的用户

## 环境要求

建议使用 Windows 环境，并安装以下工具：

- TeX Live 或 MiKTeX
- XeLaTeX
- BibTeX
- latexmk（推荐）
- VS Code 或其他文本编辑器
- Codex（用于本地 AI 协作）

项目中的中文字体文件已经放在 `latex_document/` 目录下，模板会直接引用：

- `simsun.ttc`
- `simhei.ttf`
- `STKAITI.TTF`

因此在多数 Windows 环境中可以直接编译。如果在其他系统中使用，请根据系统字体情况调整 `CUGThesis.cls` 中的字体配置。

## 快速开始

克隆仓库：

```bash
git clone https://github.com/yjfingit/CUGThesis.git
cd CUGThesis/latex_document
```

使用 `latexmk` 编译：

```bash
latexmk -xelatex Thesis.tex
```

如果需要手动编译，可按下面顺序执行：

```bash
xelatex Thesis.tex
bibtex Thesis
xelatex Thesis.tex
xelatex Thesis.tex
```

编译完成后会生成：

```text
latex_document/Thesis.pdf
```

## 如何改成自己的论文

1. 修改 `latex_document/Thesis.tex` 中的论文基本信息：

```tex
\title{论文题目}
\author{作者姓名}
\date{日期}
\school{学院名称}
\classnum{专业}
\stunum{学号}
\instructorone{指导教师}
\instructoronelevel{教师职称}
```

2. 在 `Thesis.tex` 中替换摘要、关键词和正文内容。

3. 将论文图片放入：

```text
latex_document/Figures/
```

并在正文中通过 `\includegraphics` 引用。

4. 将参考文献 BibTeX 条目放入：

```text
latex_document/Bibs/mybib.bib
```

正文中使用：

```tex
\cite{文献key}
```

5. 重新运行编译命令，检查目录、图题、表题、参考文献和 PDF 页面效果。

## AI 辅助写作流程

本项目推荐的写作顺序不是直接让 AI 从零生成整篇论文，而是先建立真实材料，再让 AI 帮助整理表达：

1. 准备学校论文模板、论文结构和基本选题
2. 先用 Markdown 整理实验过程、数据、截图、参考文献和个人思考
3. 优先完成最能体现真实工作量的实验与结果分析章节
4. 基于实验事实反向补全绪论、相关理论、方法设计和系统实现
5. 人工核查 AI 生成内容，避免虚构实验、数据和参考文献
6. 将稳定后的 Markdown 内容迁移到 `Thesis.tex`
7. 使用 BibTeX 管理参考文献，使用 `Figures/` 管理图像
8. 编译 LaTeX，逐页检查最终 PDF

## 学术诚信提醒

AI 适合用于结构整理、语言润色、格式转换、代码辅助和资料归纳，但不能替代学生完成真实研究工作。

使用本流程时，请务必遵守以下原则：

- 不使用 AI 虚构实验过程
- 不使用 AI 伪造实验数据
- 不使用 AI 编造参考文献
- 不把未经核查的 AI 输出当作事实
- 不隐瞒学校或导师要求披露的 AI 使用情况
- 最终论文内容应由作者本人审阅、核验和负责

## 常见问题

### 编译时中文字体报错怎么办？

请检查 `latex_document/` 下是否存在以下字体文件：

```text
simsun.ttc
simhei.ttf
STKAITI.TTF
```

如果你的系统无法识别这些字体，请修改 `CUGThesis.cls` 中的 `\setCJKmainfont`、`\setCJKsansfont` 和 `\setCJKmonofont` 配置。

### 参考文献没有显示怎么办？

请确认：

- `Bibs/mybib.bib` 中存在对应 BibTeX 条目
- 正文中使用了正确的 `\cite{key}`
- 已经运行过 `bibtex Thesis`
- XeLaTeX 至少在 BibTeX 后再次运行两次

### 图片无法显示怎么办？

请确认图片位于 `latex_document/Figures/` 目录，并且 `Thesis.tex` 中包含：

```tex
\graphicspath{{Figures/}}
```

图片文件名建议避免空格和特殊符号，以减少跨平台编译问题。

## 说明

本项目主要用于论文写作流程教学和 LaTeX 模板使用示范。实际提交论文前，请以学院、学校和导师发布的最新格式要求为准，并对正文、图表、参考文献和声明页进行人工复核。

## 致谢

本项目参考并使用了 CUGThesis 相关 LaTeX 模板思路，感谢原模板作者和开源社区对高校论文排版工作的贡献。
