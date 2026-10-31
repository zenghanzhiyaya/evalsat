# LSAT 错题分析台 · LSAT Error Analyzer

LSAT 备考工具：题型指南、可分级的题库、随机刷题，以及模考和日常练习的弱项分析。中英文界面，单个 HTML 文件，无需构建。

## 功能

- **概览**：模考分析（分数走势、模考常错题型、错因）和日常练习分析（正确率走势、各题型 / 难度 / 科目正确率、用时、薄弱点建议）
- **刷题**：按难度（易 / 中 / 难 / 混合）、科目、题型、范围随机出题，计时、即时判分、逐题回顾、错题重刷
- **题型指南**：LR 5 个题型族、RC 4 类，共 28 种题型的识别信号、做法和常见陷阱
- **题库**：导入 JSON / CSV / TSV 文件，可手动调整每道题的题型和难度
- **记录模考**、**历史**、**设置**（语言、默认题数、目标用时、导出备份）

## 本地运行

直接用浏览器打开 `index.html`，或在目录里起一个静态服务器：

```bash
python3 -m http.server 8000
```

## 部署

仓库自带 GitHub Pages 工作流（`.github/workflows/pages.yml`）。推送到 `main` 后，在仓库 **Settings → Pages → Build and deployment → Source** 选 **GitHub Actions**，之后每次推送都会自动发布。

也可以直接部署到 Vercel、Netlify、Cloudflare Pages 等任何静态托管平台：根目录就是站点目录，不需要构建命令。

## 独立部署与 Claude 版本的区别

这个页面最初是作为 Claude 里的 Artifact 构建的。独立部署时：

- **数据保存在浏览器的 localStorage 里**，只在当前浏览器有效。换设备前用 **设置 → 导出 JSON** 备份。
- **AI 功能不可用**：PDF / 纯文本 / 截图的 AI 识别、AI 自动补全难度和题型，都依赖 Claude 的运行环境。独立部署时只能导入 JSON / CSV 格式的题目。
- 在线字体来自 Google Fonts，PDF 解析库来自 cdnjs。

## 题库文件格式

CSV 第一行为表头：

```
section,type,difficulty,stimulus,question,A,B,C,D,E,answer,explanation
```

- `section`：LR 或 RC
- `type`：题型代码、英文名或中文名，如 `Flaw`、`Necessary Assumption`、`必要假设`
- `difficulty`：易 / 中 / 难、easy / medium / hard，或 1–5
- `answer`：A–E

JSON 为同样字段的对象数组，选项可以写成 `"choices": [...]`。

## 关于示例题

内置的 17 道示例题和示例数据均为原创，仅用于演示。LSAT 是 LSAC 的注册商标，本项目与 LSAC 无关。
