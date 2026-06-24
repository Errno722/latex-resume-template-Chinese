# LaTeX 中文简历模板

一个面向中文求职场景的 LaTeX 简历模板，支持按岗位维护不同版本的项目经历和技能模块。默认使用 XeLaTeX 编译，适合在本地或 Overleaf 上快速生成针对不同岗位的 PDF 简历。

## 特性

- 岗位版本切换：内置 `job_1` / `job_2` 两套项目经历和技能示例。
- 模块化维护：个人信息、教育背景、工作经历、项目经历、技能分文件管理。
- 中文友好：使用 `xeCJK`、中文断行设置和跨平台字体回退。
- 一键构建：提供 `latexmkrc` 和 `Makefile`，默认输出到 `build/`。
- 简历排版：左侧正文、右侧日期/地点的紧凑布局，适合一页简历。

## 目录结构

```text
.
├── Makefile
├── latexmkrc
├── README.md
└── Template
    ├── main.tex
    ├── preamble.tex
    ├── profile.tex
    ├── resume-job-1.tex
    ├── resume-job-2.tex
    ├── education.tex
    ├── work_experience.tex
    ├── projects
    │   ├── job_1.tex
    │   └── job_2.tex
    └── skills
        ├── job_1.tex
        └── job_2.tex
```

## 快速开始

本地需要安装完整 LaTeX 环境，并确保可使用 `xelatex` 和 `latexmk`。

```bash
make
```

默认生成 `job_1` 版本。输出文件位于 `build/`。

生成指定岗位版本：

```bash
make job JOB=job_1
make job JOB=job_2
```

清理构建产物：

```bash
make clean
```

## 在 Overleaf 中使用

1. 上传整个项目目录。
2. 将编译器设置为 `XeLaTeX`。
3. 将主文件设为 `Template/main.tex`，或直接编译 `Template/resume-job-1.tex` / `Template/resume-job-2.tex`。
4. 在 `Template/profile.tex` 中替换姓名、邮箱、电话、所在地和个人链接。

## 切换岗位版本

推荐直接编译岗位入口文件：

- `Template/resume-job-1.tex`
- `Template/resume-job-2.tex`

也可以在 `Template/main.tex` 中修改默认值：

```tex
\providecommand{\jobtype}{job_1}
```

新增岗位版本时，按以下步骤操作：

1. 在 `Template/projects/` 下新增 `job_x.tex`。
2. 在 `Template/skills/` 下新增 `job_x.tex`。
3. 复制一个入口文件，例如 `Template/resume-job-2.tex`，把 `\jobtype` 改成 `job_x`。

## 编辑内容

- 个人信息：`Template/profile.tex`
- 教育背景：`Template/education.tex`
- 工作经历：`Template/work_experience.tex`
- 项目经历：`Template/projects/job_*.tex`
- 技能：`Template/skills/job_*.tex`
- 样式和字体：`Template/preamble.tex`

## 编译说明

该模板依赖 XeLaTeX。不要使用 pdfLaTeX 编译，否则中文字体和断行会失败。

模板会按顺序尝试常见字体：

- 英文字体：`TeX Gyre Heros`、`Helvetica`、`Latin Modern Sans`
- 等宽字体：`Latin Modern Mono`、`Menlo`、`Courier New`
- 中文衬线字体：`Noto Serif CJK SC`、`Source Han Serif SC`、`Songti SC`、`SimSun`
- 中文无衬线字体：`Noto Sans CJK SC`、`Source Han Sans SC`、`PingFang SC`、`SimHei`

如果你的环境仍然缺字体，可以在 `Template/preamble.tex` 中替换为系统已安装的字体。
