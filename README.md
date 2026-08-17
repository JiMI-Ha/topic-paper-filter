# topic-paper-filter

一个可公开复用的 Claude Code 技能与 Quartz 研究网站骨架，用于把研究 Topic、论文 Reading Cards、Lens 筛选视角和可解释排序分开维护。

> 本仓库只包含网站框架、模板、文档、发布工作流和 `topic-paper-filter` skill；不包含原始研究网站的具体论文内容、专题页面或构建产物。

## 包含内容

- `.claude/skills/topic-paper-filter/SKILL.md`：按 Topic 搜索、总结并排序论文的 Claude Code skill。
- `quartz/`：Quartz 静态知识库网站代码。
- `content/index.md`：占位首页，可替换为自己的研究工作台首页。
- `content/templates/`：Reading Card 和 Topic 页面模板。
- `docs/`：研究工作台模型、工作流、评分与公开内容政策。
- `.github/workflows/`：内容检查与 GitHub Pages 部署工作流。

## 快速开始

要求：Node.js 22+、npm 10+。

```bash
npm ci
npm run dev
```

构建、内容校验和格式检查：

```bash
npm run validate:content
npm run check:workspace
npm run build
```

## 使用 skill

把 `.claude/skills/topic-paper-filter` 放在 Claude Code 项目的 `.claude/skills/` 下，然后提出研究 Topic，例如：

```text
Use topic-paper-filter to find and rank papers about LLM over-refusal evaluation.
```

skill 会输出：

- Topic understanding
- 推荐排序指标
- Ranked direct papers
- Adjacent / diagnostic references
- Read first
- Uncertainty and next questions

## 添加自己的内容

1. 复制 `content/templates/topic.md` 创建一个 Topic 页面。
2. 复制 `content/templates/paper.md` 为论文建立 Reading Card。
3. 在 Topic 中记录 Lens、证据空白和推荐阅读顺序。
4. 运行 `npm run check:workspace` 与 `npm run build`。

注意：不要提交原始 PDF、密钥、个人信息、内网链接或非公开业务资料。

## 发布到 GitHub Pages

仓库内置 GitHub Pages 工作流。推送到 `main` 后，GitHub Actions 会执行 `npm ci`、构建 Quartz，并部署 `public/`。

首次启用时，在 GitHub 仓库设置中选择：

```text
Settings → Pages → Build and deployment → GitHub Actions
```

如使用 GitHub Pages 项目站点，请确认 `quartz.config.ts` 中的 `baseUrl` 与仓库地址匹配。

## License

项目级代码、模板与文档以 [MIT License](LICENSE.txt) 发布；Quartz 上游代码继续遵循其原有版权与许可证说明。
