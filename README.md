# paper-to-ppt-planning

一个用于“把论文内容规划成适合演讲的 PPT 方案”的 Codex skill。

它的职责不是直接生成最终 `.pptx` 文件，而是先完成更关键的上游规划工作：

- 明确汇报目标
- 判断听众背景
- 选择叙事路线
- 设计页级结构
- 输出可继续制作的 Markdown 讲稿或 PPT 大纲

## 适用场景

适合下面这些请求：

- 根据论文整理组会或课程汇报
- 把论文笔记、摘要或 Markdown 稿件改成 PPT 结构
- 在问题驱动、技术演进、结果导向几种叙事路线之间做选择
- 重写同一篇论文，使其适配不同听众和汇报场景

不适合优先用在这些任务上：

- 只做论文总结
- 结构已经确定，只需要直接编辑 `.pptx`
- 只做视觉美化或模板替换

## 输入与输出

常见输入：

- 论文 PDF
- 论文链接
- 摘要或正文摘录
- 已有 Markdown 讲稿
- 用户自己的读书笔记

默认输出：

- 结构化 Markdown 规划稿
- 逐页标题与正文建议
- 必要的配图建议
- 讲解提示

如果环境里还有 `pdf` 或 `pptx` 相关 skill，可以在此基础上继续串联读取论文或生成演示文件；如果没有，这个 skill 也可以独立工作。

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

## 文件说明

- `SKILL.md`
  具体的 skill 定义、触发条件、工作流和约束
- `references/route-patterns.md`
  常见叙事路线与适用场景
- `references/page-structure-template.md`
  默认页级 Markdown 输出模板
- `references/ml-paper-guidelines.md`
  机器学习论文场景下的补充约束

## 安装

将整个目录复制到本机 Codex skills 目录即可，例如：

```powershell
Copy-Item -Recurse -Force .\paper-to-ppt-planning C:\Users\admin\.codex\skills\
```

## 示例

例如用户说：

“帮我把这篇论文整理成 12 页组会汇报，听众是有机器学习基础但没读过原文的同学。”

这个 skill 会优先帮助确定：

- 应该采用哪条叙事路线
- 每一页承担什么讲述任务
- 哪些背景必须讲，哪些可以压缩
- 最终适合交给 PPT 制作阶段的结构化内容
