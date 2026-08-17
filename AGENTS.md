# topic-paper-filter 发布规则

## 触发条件

当用户提供一篇论文（PDF、本地文件、arXiv 或论文链接），并要求以下任一内容时，自动执行完整整理流程：

- `motivation method 和 results`
- `motivation、method、results`
- “整理/总结论文的动机、方法和结果”或语义等价的请求

如果用户明确说“不要发布”“只在聊天里回答”或“先别上传”，则只提供分析，不改动网站。

## 论文分析要求

1. 阅读完整相关章节，不得只依赖摘要。
2. 核对方法公式、实验设置、主结果、消融实验和局限。
3. 不得编造论文中没有的数字、结论或因果解释。
4. 对不显著、样本量较小或证据有限的结论明确降级表述。
5. 页面至少包含：
   - 基本信息与原文链接
   - Motivation
   - Method
   - Experimental Setup
   - Results
   - Ablation / Robustness（论文提供时）
   - Sensitivity / Boundary Conditions（论文提供时）
   - Limitations
   - Takeaways
   - Citation（能够可靠获得时）

## 网站发布流程

网站仓库为当前仓库，默认线上地址为 <https://jimi-ha.github.io/topic-paper-filter/>。

每次发布内容后：

1. 按主题分类创建独立 Markdown 页面，文件名使用稳定、简洁的英文 slug。
2. 使用完整 frontmatter，至少包含 `title`、`created`、`published`、`modified`、`type`、`tags` 和 `source_url`。
3. 新 Topic 优先从 `content/templates/topic.md` 复制模板。
4. 新论文 Reading Card 优先从 `content/templates/paper.md` 复制模板。
5. 更新相关 Topic 或索引页面；不要覆盖无关历史内容。
6. 运行：
   - `npm ci`（仅在依赖缺失时）
   - `npm run build`
   - `npx tsc --noEmit`
   - 对本次修改文件运行 Prettier 检查
7. 创建清晰的 Git commit，并在用户授权后推送。

## 发布安全与失败处理

- 推送前确认远程仓库仍是预期的公开仓库。
- 保留用户已有的未提交修改，不覆盖或回滚无关内容。
- 构建、测试、推送或部署失败时，不宣称发布成功。
- 不把原始本地 PDF、密钥、个人信息、内网链接或临时渲染文件提交到仓库；网站只发布整理后的论文笔记和公开来源链接。
