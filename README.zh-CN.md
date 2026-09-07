# Mobile to HarmonyOS Porting 🚀

> [English](README.md) | 简体中文

这是一个以证据为核心的 Codex Skill，用于将 Android、iOS、Flutter、React Native
及共享原生能力，分阶段迁移或同步到既有 HarmonyOS 应用中。

![分阶段迁移顺序](assets/porting-order.svg)

## ✨ 不可打破的迁移顺序

**先迁移页面 UI 分组，再迁移功能分类。**

每个小页面分组验收通过后，才可以迁移它的新功能。页面视觉完成并不等于数据、硬件、
服务、权限或生命周期行为已经验证。

除非用户明确授权例外，所有 UI 素材和可见设计决策必须来自被迁移的源项目快照。Skill
禁止生成、搜索、购买、替换或自行创作 UI 素材。若源素材缺失、访问或授权边界不清，
或 HarmonyOS 无法等效呈现，必须停止并记录为 `BLOCKED`，不得自行补一个替代方案。

## 🧭 Skill 提供什么

- 按页面 UI 与功能分类分阶段推进的迁移手册；
- 源端到目标端的证据、验收与测试模板；
- 对破坏性数据、平台能力不等效、发布证据过期、取消竞态和共享工作区风险的停止条件；
- Codex 插件清单与可独立安装的 Skill 文件夹。

![证据门禁](assets/evidence-gate.svg)

它**不会**自动翻译源代码、提供厂商私有协议实现，或把缺失的平台/固件证据包装成通过。

## 📦 安装

### 方式一：通过 Codex 安装（推荐）

在新的 Codex 对话中粘贴下面这句话：

```text
$skill-installer install https://github.com/yisen171121/mobile-to-harmonyos-porting/tree/main/skills/mobile-to-harmonyos-porting
```

Codex 会把这个公开 Skill 下载到本地 Skill 目录。通常下一轮会自动识别；如果没有出现，
请重启 Codex。

### 方式二：仅用于一个项目

将仓库内的 `skills/mobile-to-harmonyos-porting/` 文件夹复制到：

```text
<你的项目>/.agents/skills/mobile-to-harmonyos-porting/
```

这样 Skill 会随项目一起版本管理，并且在该仓库内启动 Codex 时自动可用。

### 方式三：安装到当前用户目录

将同一个文件夹复制到用户 Skill 目录：

```text
~/.agents/skills/mobile-to-harmonyos-porting/
```

如果希望它跨项目可用，请选择这种方式。复制后若未出现，请重启 Codex。

## ▶️ 安装后调用

```text
$mobile-to-harmonyos-porting migrate this source snapshot page by page, then function category by function category.
```

也可以直接描述符合条件的迁移任务，Codex 会根据 Skill 的描述自动选择它；如需确保本轮
加载，请显式使用 `$mobile-to-harmonyos-porting`。

## ✅ 所需输入

- 可读取的上游源项目快照及其访问/授权边界；
- 已存在的 HarmonyOS 目标项目与当前 Git 状态；
- 本次请求的页面与功能分类范围；
- 支持的设备、系统、SDK 与固件；
- 当行为与版本相关时，对应的官方 API、SDK 与协议资料；
- 当验收需要时，测试真实硬件或服务的授权。

## 🔒 隐私与安全

不要把 API Key、Token、证书、私有端点、客户数据、专有源代码、生产原始日志、
设备标识、私有协议内容或源项目 UI 素材写入迁移笔记、测试、Issue 或 Pull Request。
请在目标项目中核验源素材的授权与访问边界；这个公开仓库不再分发任何产品素材。

## 🧪 验证状态

`v0.1.0` 已完成结构、清单、内容安全与场景覆盖静态校验。独立的新上下文压力场景回放
记录在 [`evals/v0.1.0-results.md`](evals/v0.1.0-results.md)；完成前不得将 Skill 描述为
“已通过行为验证”。

## ⚖️ 许可证

可任选 [MIT](LICENSE-MIT) 或 [Apache-2.0](LICENSE-APACHE) 双许可证。
