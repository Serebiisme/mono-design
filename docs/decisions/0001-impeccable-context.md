# 0001 Impeccable 安装与文档连接

日期：2026-10-22
状态：采用

## 背景

项目已有产品、设计与协作规范。用户要求安装并配置 Impeccable、连接现有文档、验证可用性，暂不编写组件代码。

## 选择

- 使用 Codex skill-installer，从 `pbakaus/impeccable` 的 `.agents/skills/impeccable` 安装到本机 `/Users/bytedance/.codex/skills/impeccable/`。
- 固定来源提交 `8644175285360c166e57b1e35ecadfbc85ff5209`，技能版本 `4.7.0`，引擎版本 `0.1.16`。
- 根目录 `PRODUCT.md` 和 `DESIGN.md` 分别以相对符号链接指向现有产品和设计文档。
- 在源文档补充必要的机器可识别字段和章节，保持现有产品范围、视觉方向及技术栈待定状态。
- 不创建产品工程、不安装产品依赖、不配置 live 浏览器、不启用编辑钩子。

## 原因与备选

直接安装官方技能及配套脚本，可使用自带引擎读取与诊断项目，不需要初始化 npm 工程。固定提交便于复查来源。

符号链接使工具入口和现有文档指向同一内容。另存摘要副本需要长期同步，只有入口链接的 Markdown 包装文件也不能保证被工具完整读取，因此采用文件系统链接。

官方 `npx impeccable install` 是另一条安装入口。本机已有 skill-installer，本次统一通过该技能安装，不重复安装同一技能或修改其他客户端设置。

## 代价

- 用户级技能可供本机其他项目使用；新机器需单独安装，绝对安装路径不能直接复用。
- 协作者的文件系统与 Git 检出方式需要支持符号链接。使用替换式写入工具时，应编辑解析后的源文件，保留兼容链接。
- 当前设计文档仅包含初始约定，没有组件、设计变量源码或浏览器验证；诊断无发现不代表视觉或可访问性验收通过。
- `shape` 是 AI 工作流程；引擎与入口验证不能代替需求访谈和方案确认。

## 重审条件

- 换用操作系统、安装目录或客户端，导致技能发现和符号链接行为变化。
- Impeccable 升级后更改上下文解析、schema 或命令入口。
- 项目开始实现，需要接入浏览器预览、编辑钩子或机器可读设计变量。

## 复现

```sh
python3 /Users/bytedance/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo pbakaus/impeccable \
  --path .agents/skills/impeccable \
  --ref 8644175285360c166e57b1e35ecadfbc85ff5209 \
  --dest /Users/bytedance/.codex/skills --method download
chmod u+x /Users/bytedance/.codex/skills/impeccable/scripts/impeccable
```

仅在目标目录不存在时安装，禁止为重复安装直接覆盖已有技能。首次运行启动器可能下载对应版本引擎；官方启动器使用 SHA-256 sidecar 校验新下载文件。

官方来源：[Impeccable 固定提交](https://github.com/pbakaus/impeccable/tree/8644175285360c166e57b1e35ecadfbc85ff5209)。验证命令与结果见[验证记录](../tooling/impeccable-verification.json)。
