# 设计工具协作流程

将 UI UX Pro Max 与 Impeccable 用于设计研究、方案推敲和质量改进。两者的输出需要结合项目场景筛选，最终有效约定统一维护在现有项目规范中。

## 工程流程中的位置

本文是[工程开发范式](engineering.md#工程开发范式设计与开发闭环)的工具操作细则，不另建一套开发流程。Editorial 最终方向已落入[设计规范](design-system.md)；后续默认从组件任务与状态出发，使用最少必要的工具步骤，采纳结果写回现有规范，任务状态集中维护在 roadmap。

## 分工

| 阶段 | 优先工具 | 产出 |
| --- | --- | --- |
| 建立视觉方向 | UI UX Pro Max | 风格、配色、排版和密度的候选及适用理由 |
| 规划组件与场景 | Impeccable shape | 任务路径、信息层级、状态和边界方案 |
| 专项查证 | UI UX Pro Max | 焦点、表单、文本溢出等具体问题的参考建议 |
| 评审现有预览 | Impeccable critique、audit | 设计问题与技术质量发现，注明证据和优先级 |
| 有针对性地改进 | Impeccable polish、harden、distill | 一致性、边界行为或视觉简化的具体改动 |

这是本项目的协作安排。按问题选择工具，每个小改动无需执行完整流程。两个工具都不能替代真实的行为验证和浏览器验收。

“建立视觉方向”只在用户要求新增或重审方向时使用；Editorial 已选定，日常组件工作从方案、专项查证和预览评审开始。

## 项目约束

- 主要对象是桌面后台、组件及其预览，目标是操作效率、可读性和一致性。
- 对 Impeccable 的后台页面方案使用 Operate 语境；组件文档页面使用 Read 语境。未来若制作官网，再独立讨论展示与转化目标。
- 遵守 Editorial 的暖米色／柔黑、衬线标题／系统无衬线正文、直角细线和单色反馈。语义独立、形状与文字明确，不自动引入彩色强调或另一套候选风格。
- 针对后台筛选、表格和表单筛选建议，排除与目标无关的 Hero、营销 CTA、装饰动效和行业模板。
- 字号、点击区域、密度与响应式建议结合桌面操作场景验证；兼顾可访问性，避免直接复制移动端或营销页的整套参数。
- 技术栈尚未确定，检索时不指定虚构的框架，也不据此安装样式或动效依赖。

## 规则与文档归属

用户明确要求和项目规范约束工具建议。发现冲突时，写清冲突、影响和处理理由；需要修改项目规范时按授权范围同步修改。

| 内容 | 有效来源 |
| --- | --- |
| 定位、用户、范围 | [产品定位](product.md) |
| 视觉与交互原则 | [设计规范](design-system.md) |
| 设计变量数值 | 实现前参考设计规范；实现后以 `src/tokens/` 为准 |
| 组件 API 和具体行为 | 对应组件目录的 README |
| 工程与验证约定 | [工程约定](engineering.md) |
| 任务、验收及工具接入进度 | [开发进度](roadmap.md) |

工具生成的候选和评审发现属于参考材料。采纳的结论写回上述来源，重要权衡进入决策记录。

## UI UX Pro Max：本机使用

本机技能入口为 `/Users/bytedance/.codex/skills/ui-ux-pro-max/SKILL.md`，实际目录为 `/Users/bytedance/.agents/skills/ui-ux-pro-max/`。这是本机路径，其他协作者需定位自己的安装目录。

先读取技能，再运行其中的检索脚本。以下命令已在本机执行，不会向项目保存设计候选：

```sh
python3 /Users/bytedance/.agents/skills/ui-ux-pro-max/scripts/search.py \
  "enterprise dashboard minimal" \
  --design-system --variance 2 --motion 2 --density 7 \
  -p "Mono Design" -f markdown
```

三个参数分别控制风格变化、动效程度和视觉密度，都是检索条件，不代表项目已经采用相应尺寸或效果。建议从低变化、低动效、适合后台的密度开始比较。

已有设计基线后，针对具体问题使用专项检索，例如：

```sh
python3 /Users/bytedance/.agents/skills/ui-ux-pro-max/scripts/search.py \
  "keyboard focus modal" --domain ux
```

专项示例尚未执行。使用时先核对结果是否回答了当前问题；空结果或不匹配时，收窄查询或显式指定领域重试一次。仍不适用时说明未找到经核实的匹配，采用项目约定和明确标注的一般建议。

本项目默认不使用 `--persist` 自动创建另一份设计主文档。先审阅输出，再将采纳结论整理到现有设计规范；如以后需要原生持久化目录，需明确它与现有文档的归属和同步方式，避免两套主规范并行。

## Impeccable：本机使用

本机通过 Codex 的 skill-installer 安装官方技能到 `/Users/bytedance/.codex/skills/impeccable/`。来源版本及选择依据见[接入决策](decisions/0001-impeccable-context.md)，当前状态见 roadmap。

### 文档连接

- `PRODUCT.md` → `docs/product.md`：相对符号链接，直接读取同一份产品文档。
- `DESIGN.md` → `docs/design-system.md`：相对符号链接，直接读取同一份设计文档。
- 产品文档提供官方 schema 标记、`Platform` 和 `Stack` 字段；平台为 `web`，技术栈保持待定。
- 设计文档补充工具可识别的 `Colors`、`Typography`、`Components` 章节，读取已确认的 Editorial 规范，并保留变量和组件尚未实现的事实。

直接维护 `docs/` 下的源文件；使用原子替换类编辑工具时先解析符号链接目标，避免覆盖链接。新机器或不支持符号链接的检出环境需先检查这两个入口能否正确解析。

### 命令与验证

从项目根目录运行实际安装目录中的脚本：

```sh
/Users/bytedance/.codex/skills/impeccable/scripts/impeccable engine-probe
/Users/bytedance/.codex/skills/impeccable/scripts/impeccable context
/Users/bytedance/.codex/skills/impeccable/scripts/impeccable doctor --json
/Users/bytedance/.codex/skills/impeccable/scripts/impeccable signals
```

每次设计会话按技能要求加载一次 context；配置变更后按验证需要重新检查。`context` 用于实际读取上下文，不能用 `context --help` 当作只查看帮助的命令，本次实测它仍会读取项目。

`shape`、`critique` 等是 AI 技能工作流程，不是引擎的同名终端子命令。终端 `help` 用于确认命令目录，实际工作通过 Codex 调用技能并阅读对应 playbook。

在下一轮对话中，新安装技能可由 Codex 发现。可以输入：

```text
使用 $impeccable 的 shape 工作流程，阅读现有项目规范，规划 Dialog 的交互与验收要求，先不写组件代码。
```

其他 AI 客户端支持的命令形式示例：

```text
/impeccable shape 后台筛选与弹窗表单的交互方案，遵循当前规范，仅输出方案。
/impeccable critique 指定组件预览，先列问题、证据和优先级。
/impeccable audit 指定预览的键盘、焦点、溢出及响应式问题。
/impeccable polish 指定组件的间距、对齐与状态一致性，保留现有 API。
/impeccable harden 指定表单的错误恢复、重复提交与长文本行为。
/impeccable distill 指定预览中多余的装饰，保留状态提示与操作入口。
```

具体入口以实际安装版本和客户端为准。当前仅验证引擎、文档读取、诊断、项目状态及 shape 入口与说明文件，未开展完整 shape 访谈或组件设计；详细证据见[验证记录](tooling/impeccable-verification.json)。

当前没有组件实现，不能通过 `document` 从源码提取已实现的视觉系统。自动编辑钩子和 live 浏览器功能暂不启用，待有工程和运行页面时再接入；未持久化与当前任务无关的图片生成或展示页构建偏好。

## 一次组件迭代

1. 阅读产品、设计、工程规范和当前组件规范，明确本轮目标。
2. 缺少视觉方向时，用 UI UX Pro Max 生成候选；已有基线时只查具体缺口。
3. 用 Impeccable shape 推敲任务路径、交互状态和边界，将结论写入组件规范。简单且已明确的交互可直接沿用现有约定。
4. 获得组件实现任务后，按规范完成实现和状态预览。
5. 使用 critique 或 audit 定位实际问题，再按问题选择 polish、harden 或 distill。
6. 执行工程检查与浏览器验证，更新组件规范和 roadmap。工具报告、人工检查与自动化测试分别记录。

当前只开展文档和流程准备，后续组件实现及预览验收尚未开始。

## 可直接使用的提示词

设计基线：

> 阅读项目规范，沿用已确认的 Editorial 风格。仅针对本轮组件的明确问题使用 UI UX Pro Max 专项检索，说明哪些建议适用、哪些与后台场景或单色规范冲突；采纳结论写回现有规范，不重新选择视觉方向或创建另一份设计系统。

组件方案：

> 在 Impeccable 可用时使用 shape，依据当前设计规范完善 Dialog 的交互方案。覆盖打开、关闭、焦点进入与返回、滚动、加载和错误状态，填写组件规范，先不写代码。技能不可用时明确说明。

已有预览的改进：

> 按现有设计规范评审指定组件预览，先用 critique 或 audit 列出有证据的问题，再处理影响最大的项。只对缺少依据的问题用 UI UX Pro Max 专项检索，保留公共 API，并报告实际验证范围。

## 官方参考

- [Impeccable 项目与命令说明](https://github.com/pbakaus/impeccable)
- [Impeccable 技能中的模式与上下文约定](https://github.com/pbakaus/impeccable/blob/main/.agents/skills/impeccable/SKILL.md)
- [UI UX Pro Max 中文说明](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/README.zh.md)

工具会演进；接入或升级时重新核对官方说明和本机技能，不能仅依赖本文的命令示例。
