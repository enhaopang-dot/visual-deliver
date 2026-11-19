# AI 生图提示词全局规则

库文件：`D:/Claude/配置/.claude/config/ai-prompts.yaml`

## 组合规则

1. 用户明确指定场景 → 从 `scenes` 取模板。
2. 否则默认组合：`base.quality` 必带 + 一个 `content` + 1-2 个 `style` + 一个 `composition` + 一个 `lighting` + 可选 0-2 个 `design`。
3. 用户专属细节顶层覆盖，不写入库。
4. 负面提示词默认带 `base.negative`。
5. 项目存在 `ai-prompts-overrides.yaml` 时覆盖全局库对应键。
6. 最终 prompt 语义顺序：内容主体 → 风格技法 → 构图镜头 → 光影氛围 → 设计强化 → 画质渲染。

## A/B 迭代

- 同一主题 2-3 张对比时只变一项变量。
- 记录日期、任务、变量项、A/B 组合、seed、生成路径到 `D:/Claude/配置/.claude/config/ai-prompts-changelog.md`。
- 每月 review 一次库：删除 30 天未调用片段，合并重复，更新默认推荐。

## 禁止

- 不复用库而直接拼凑提示词（用户明确要求除外）。
- 把项目专属细节写入全局库。
- 不经验证一次性引入过多新分类。
- 不记录 A/B 结果就修改默认片段。

## 质量自检

分层组合、含 `base.quality`、负面提示词已带、专属细节已加入、画幅与 `composition` 一致、必要时 `design` 强化、超过 200 字则精简。

## Kolors 注意

- 优先中文提示词，关键风格词可中英并用。
- 超过 200 字可能丢失尾部信息，需精简。
- 负面提示词不必过度堆砌。

## 版权边界

- `design.art_reference` 仅作风格指向，不复制作品。
- 商业用途避免使用在世艺术家姓名生成可商用内容。
