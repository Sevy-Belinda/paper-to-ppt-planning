# paper-to-ppt-planning

一个用于“把论文转成可讲的 PPT 方案”的 Codex skill。

它的重点不是直接生成幻灯片文件，而是先完成真正重要的上游工作：

- 明确汇报目标
- 判断听众背景
- 选择叙事路线
- 设计页级结构
- 输出适合后续制作的 PPT 策划稿

这个 skill 适合研究汇报、组会报告、课程展示、答辩准备、论文讲稿整理等场景。

## 为什么名称里要有 planning

这个 skill 的核心职责是“规划与结构设计”。

如果本机同时具备 PDF 与 PPTX 相关能力，它可以作为入口协调完整流水线；但如果环境中缺少这些能力，它仍然应该先完成策划工作，而不是假装自己一定能直接产出 `.pptx` 文件。

因此名称中保留 `planning` 更准确，也更能表达它是上游策划 skill，而不是纯文件生成器。

## 环境与工具检查机制

在开始执行任务前，这个 skill 会先检查当前工作区是否安装了或可调用：

- 处理 PDF 的相关 skill 或工具
- 处理 PPTX 的相关 skill 或工具
- 通用文档处理相关 skill 或工具

### 推荐下载来源

缺少通用能力时，优先从下面的仓库下载：

- `https://github.com/anthropics/skills`
  推荐使用其中的：`pdf`、`docs`、`pptx`

如果任务属于专业科研领域，或者用户需要更强的科研场景支持，可进一步推荐：

- `https://github.com/K-Dense-AI/scientific-agent-skills`

### 如果工具齐全

直接执行全自动流水线：

`读取 PDF -> 规划大纲 -> 生成 PPTX`

### 如果缺少工具

先暂停自动流水线，并礼貌提示用户当前本地缺少相关能力。

推荐交互方式：

- 提示检测到本地没有 `pdf`、`docs`、`pptx` 中的一项或多项
- 询问用户是否需要下载

如果用户愿意下载：

- 优先从 `anthropics/skills` 下载 `pdf`、`docs`、`pptx`
- 如果任务明显偏科研专业场景，可补充推荐 `K-Dense-AI/scientific-agent-skills`
- 下载完成后继续原始需求

如果用户不想下载：

- 提示用户可以直接提供 PDF 文本
- 然后先输出适合制作 PPT 的 Markdown 结构

推荐提示语：

“您可以直接把 PDF 的文本内容粘贴给我，我可以先帮您生成适合制作 PPT 的 Markdown 结构。”

## 设计目标

大多数“根据论文做 PPT”的任务，真正难的不是把内容塞进页面，而是先回答这些问题：

- 这场汇报是给谁听的
- 听众是否理解该领域背景
- 应该强调问题、方法、结果，还是技术演化
- 需要保留多少公式和实验细节
- 旧方法背景应该讲到什么程度
- 每一页在整场讲述中承担什么角色

`paper-to-ppt-planning` 的职责，就是把这些决策前置并结构化。

## 核心能力

### 1. 论文到 PPT 的策划

支持从以下输入出发：

- 论文 PDF
- 论文链接
- 摘要或正文摘录
- 用户已有笔记
- 已经写好的 Markdown 讲稿

默认输出为结构化 Markdown 策划稿，便于继续讨论、修改或后续转换为 `.pptx`。

### 2. 叙事路线设计

内置常见汇报路线：

- `problem-driven`
- `technical-evolution`
- `result-driven`

skill 不会直接替用户拍板，而是先给出 2-3 个方案、说明取舍，再推荐一个更合适的方向。

### 3. 听众与场景校准

会优先澄清这些高影响信息：

1. 任务是事实校正、结构重写，还是两者都要
2. 汇报场景是什么
3. 听众基础如何
4. 目标页数是多少
5. 是否已有偏好的叙事路线
6. 公式需要保留到什么程度
7. 是否需要配图建议

默认一次只问一个关键问题，避免需求在前期发散。

### 4. 页级结构输出

默认每页使用以下结构：

- `页标题`
- `标题`
- `页面正文`
- `配图建议`
- `图片来源`
- `讲解提示`

其中：

- `页面正文` 面向最终幻灯片
- `配图建议`、`图片来源`、`讲解提示` 面向制作和讲述过程

如果后续要真正制作 PPT，默认上页内容通常只有：

- `页标题`
- `标题`
- `页面正文`
- `配图`

## 与 `pdf` / `pptx` / `docs` 的关系

`paper-to-ppt-planning` 可以独立工作，不把其他 skill 作为硬依赖。

### 有 `pdf` skill 时

- 可先读取 PDF 内容
- 再回到 `paper-to-ppt-planning` 完成策划

### 有 `pptx` skill 时

- 可在策划完成后，把结果交给 `pptx` 做真正的演示文件

### 有 `docs` skill 时

- 可辅助做文档理解、整理和跨格式处理
- 作为 PDF 与 PPTX 之间的补充型通用能力

### 没有 `pdf` / `pptx` / `docs` 时

- 仍可正常工作
- 没有 `pdf` 时，要求用户提供论文文本、摘要、笔记或现有稿件
- 没有 `pptx` 时，输出完整 Markdown 策划稿供手工或后续自动化制作
- 没有 `docs` 时，不影响主流程，只是少了一层通用文档辅助能力

## 目录结构

```text
paper-to-ppt-planning/
  SKILL.md
  README.md
  references/
    route-patterns.md
    page-structure-template.md
    ml-paper-guidelines.md
```

## 安装

将整个 `paper-to-ppt-planning/` 目录复制到本机 Codex skills 目录即可，例如：

```powershell
Copy-Item -Recurse -Force .\paper-to-ppt-planning C:\Users\admin\.codex\skills\
```