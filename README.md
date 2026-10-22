# Mono Design

面向 B 端 Web 场景的极简主义组件库。以克制的视觉、清晰的层级和完整的交互，支持后台页面的持续开发。

项目名称暂用 Mono Design，正式包名与品牌名称在工程初始化前确定。

GitHub 仓库：[Serebiisme/mono-design](https://github.com/Serebiisme/mono-design)。仓库关联与内容推送状态见 roadmap。

## 当前状态

- 已建立项目文档和 AI 协作约定；已确认 Editorial 编辑杂志风（G 版）为最终视觉方向，正式基线见设计规范。
- 尚未初始化组件工程、安装依赖或实现组件。
- 尚无可执行的开发、测试、构建命令及预览入口。
- 技术栈、包管理器、样式方案和发布方式待确定。
- Impeccable 已接通现有文档；工具接入状态与验证边界见 roadmap。
- 建设方向已确定为全面对标成熟 B 端组件库；复杂表格、日期时间、上传和树等高级能力纳入计划，按基础与高级批次逐步交付。

## 从这里开始

| 文档 | 内容 |
| --- | --- |
| [产品定位](docs/product.md) | 用户、场景、首期范围和验收目标 |
| [设计规范](docs/design-system.md) | 极简原则、视觉基线、交互和可访问性 |
| [选定的 Editorial G 稿](docs/design-exploration/2026-10-22-stylekit-editorial/README.md) | 暖米色、柔黑、衬线标题与细分隔线；已采用 |
| [历史风格对比](docs/design-exploration/README.md) | A—K 探索索引，其他方向保留为历史参考 |
| [工程开发范式](docs/engineering.md) | 设计工具协作、组件迭代、公共 API、验证与交付 |
| [开发进度](docs/roadmap.md) | 当前阶段、任务和验收记录 |
| [建设总计划](docs/plans/component-library-build.md) | 全面建设范围、基础与高级任务、里程碑和依赖 |
| [AI 协作规则](AGENTS.md) | 开发前阅读、改动边界与交付要求 |
| [设计工具协作](docs/design-tool-workflow.md) | UI UX Pro Max 与 Impeccable 的分工、调用和规范归属 |
| [组件规范模板](docs/templates/component.md) | 新组件的使用和行为契约 |
| [决策记录](docs/decisions/README.md) | 重要选择的依据和代价 |

## 目录约定

```text
mono-design/
├── README.md
├── AGENTS.md
├── PRODUCT.md -> docs/product.md
├── DESIGN.md -> docs/design-system.md
└── docs/
    ├── product.md
    ├── design-system.md
    ├── engineering.md
    ├── design-tool-workflow.md
    ├── roadmap.md
    ├── plans/
    │   └── component-library-build.md
    ├── decisions/
    │   └── README.md
    ├── tooling/               # 工具验证记录
    └── templates/
        └── component.md
```

工程初始化后再创建 `src/tokens/`、`src/components/` 和 `playground/`。组件内部文件名随技术栈确定，组件使用与行为规范放在对应目录的 `README.md`。

## 开发方式

1. 从 roadmap 选取一个明确目标，阅读相关规范。
2. 依据 Editorial 规范明确组件用途、API、状态和验收条件；复杂交互使用 Impeccable shape，具体缺口按需使用 UI UX Pro Max 专项查证。
3. 获得实现授权后完成组件及预览；使用 critique／audit 评审实际界面，再用 polish／harden／distill 处理有依据的问题。
4. 执行工程与浏览器验证，将采纳的结论写回对应规范，更新 roadmap。详见工程开发范式。

文档使用中文；公共 API 和文件命名使用清晰、一致的英文。已实现、已验证和已发布分别记录。

UI UX Pro Max 提供设计候选和专项建议，Impeccable 用于方案推敲、评审与打磨；具体流程和接入边界见设计工具协作文档。当前工具可用性及验证结果统一记录在 roadmap。
