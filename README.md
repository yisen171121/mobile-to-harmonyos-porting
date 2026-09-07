<a id="en"></a>

<p align="center">
  <img src="assets/mobile-to-harmonyos-porting-mark.svg" width="168" alt="Mobile to HarmonyOS Porting">
</p>

<h1 align="center">Mobile to HarmonyOS Porting</h1>

<p align="center">
  <em>Port the interface exactly. Prove the behavior separately.</em>
</p>

<p align="center">
  <a href="#en"><strong>English</strong></a> &middot; <a href="#zh-cn">简体中文</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Codex-Skill-111827?style=flat-square" alt="Codex Skill">
  <img src="https://img.shields.io/badge/migration-UI%20then%20function-2F80ED?style=flat-square" alt="UI first, functional categories second">
  <img src="https://img.shields.io/badge/source%20UI-assets%20only-00A884?style=flat-square" alt="Source UI assets only">
  <img src="https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-111827?style=flat-square" alt="MIT or Apache-2.0">
</p>

<p align="center">
  <strong>UI page groups first &middot; Functional categories second</strong>
</p>

---

An evidence-led Codex Skill for incrementally porting or synchronizing Android, iOS,
Flutter, React Native, and shared-native mobile capabilities into an existing or newly
initialized HarmonyOS target.

## Start from either target state

You can start with only a non-HarmonyOS source project. The Skill first creates a
**Phase 0** target bootstrap: the smallest buildable HarmonyOS project with a recorded
package identity, module boundary, SDK baseline, and launch path. Phase 0 does not
migrate a page or feature; after it is verified, the mandatory UI-first and
function-second sequence begins.

<p align="center">
  <img src="assets/porting-order.svg" width="760" alt="Optional Phase 0 target bootstrap, then UI page groups, functional categories, and evidence">
</p>

## The rule that cannot be bypassed

Accept each small page group before porting its new behavior. A polished page is never
evidence that its data, hardware, service, permission, or lifecycle behavior works.

Unless the user explicitly authorizes an exception, every UI asset and visible design
choice must come from the migrated source snapshot. The Skill forbids generated,
searched, purchased, substituted, or creatively redesigned UI material. If the source
asset is missing, its access/license is unclear, or HarmonyOS cannot render it
equivalently, stop and record `BLOCKED`—do not invent a replacement.

## What you get

- a staged page-UI and functional-category migration playbook;
- source-to-target evidence, acceptance, and test templates;
- stop conditions for destructive data, unsupported platform behavior, stale release
  evidence, cancellation races, and shared-workspace risk;
- a Codex plugin manifest and a portable standalone Skill folder.

<p align="center">
  <img src="assets/evidence-gate.svg" width="760" alt="Evidence gate for source, target, and verification">
</p>

It does **not** translate source code automatically, provide vendor protocol
implementations, or turn missing platform/firmware evidence into a passing result.

## Install

### Option 1 — Install with Codex (recommended)

In a new Codex chat, paste this request:

```text
$skill-installer install https://github.com/yisen171121/mobile-to-harmonyos-porting/tree/main/skills/mobile-to-harmonyos-porting
```

Codex downloads the public Skill to your local skills directory. It normally discovers
the new Skill automatically; restart Codex if it is not listed on the next turn.

### Option 2 — Add it to one project

Copy the repository's `skills/mobile-to-harmonyos-porting/` folder to:

```text
<your-project>/.agents/skills/mobile-to-harmonyos-porting/
```

This keeps the workflow versioned with that project and makes it available whenever
Codex runs inside the repository.

### Option 3 — Add it for your user account

Copy the same folder to your user skills directory:

```text
~/.agents/skills/mobile-to-harmonyos-porting/
```

Use this option when you want the Skill available across projects. Restart Codex if it
does not appear after copying.

## Invoke after installation

```text
$mobile-to-harmonyos-porting migrate this source snapshot page by page, then function category by function category.
```

You can also describe a matching porting task normally; Codex can select the Skill from
its description. Use the explicit `$mobile-to-harmonyos-porting` form when you want to
guarantee it is loaded.

## Required inputs

- readable upstream source snapshot and its access/license boundary;
- an existing HarmonyOS target project, or permission to create and freeze a minimal
  Phase 0 target bootstrap;
- requested page and functional-category scope;
- supported devices, OS, SDK, and firmware;
- official API, SDK, and protocol sources when behavior is version-sensitive;
- permission to test real hardware or services when the requested evidence requires it.

## Privacy and security

Never add API keys, tokens, certificates, private endpoints, customer data, proprietary
source, raw production logs, device identifiers, private protocol material, or
source-project UI assets to migration notes, tests, issues, or pull requests. Verify
source-asset licenses and access boundaries in the target project; this public
repository contains no redistributed product assets.

## Verification status

`v0.1.0` has structure, manifest, content-safety, and scenario-coverage validation.
Independent fresh-context pressure replay is tracked in
[`evals/v0.1.0-results.md`](evals/v0.1.0-results.md) and must be completed before
treating the Skill as behaviorally proven.

## License

Dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE), at your option.

---

<a id="zh-cn"></a>

<h2 align="center">简体中文</h2>

<p align="center">
  <a href="#en">English</a> &middot; <a href="#zh-cn"><strong>简体中文</strong></a>
</p>

<p align="center">
  <strong>先完成页面 UI 分组 &middot; 再迁移功能分类</strong>
</p>

这是一个以证据为核心的 Codex Skill，用于将 Android、iOS、Flutter、React Native
及共享原生能力，分阶段迁移或同步到既有或新初始化的 HarmonyOS 目标工程中。

## 可以从两种目标状态开始

即使目前只有非 HarmonyOS 源项目，也可以开始。Skill 会先执行 **Phase 0** 目标工程初始化：
只创建可构建、可启动的最小 HarmonyOS 工程，并记录包标识、模块边界、SDK 基线与启动路径。
Phase 0 不迁移任何页面或功能；验证完成后，才开始强制执行“UI 优先、功能其次”的迁移顺序。

<p align="center">
  <img src="assets/porting-order.zh-CN.svg" width="760" alt="可选的 Phase 0 目标工程初始化，再迁移 UI 页面分组、功能分类和证据">
</p>

## 不可绕过的规则

每个小页面分组验收通过后，才可以迁移它的新功能。页面视觉完成并不等于数据、硬件、
服务、权限或生命周期行为已经验证。

除非用户明确授权例外，所有 UI 素材和可见设计决策必须来自被迁移的源项目快照。Skill
禁止生成、搜索、购买、替换或自行创作 UI 素材。若源素材缺失、访问或授权边界不清，
或 HarmonyOS 无法等效呈现，必须停止并记录为 `BLOCKED`，不得自行补一个替代方案。

## Skill 提供什么

- 按页面 UI 与功能分类分阶段推进的迁移手册；
- 源端到目标端的证据、验收与测试模板；
- 对破坏性数据、平台能力不等效、发布证据过期、取消竞态和共享工作区风险的停止条件；
- Codex 插件清单与可独立安装的 Skill 文件夹。

<p align="center">
  <img src="assets/evidence-gate.zh-CN.svg" width="760" alt="源端、目标端与验证证据门禁">
</p>

它**不会**自动翻译源代码、提供厂商私有协议实现，或把缺失的平台/固件证据包装成通过。

## 安装

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

## 安装后调用

```text
$mobile-to-harmonyos-porting migrate this source snapshot page by page, then function category by function category.
```

也可以直接描述符合条件的迁移任务，Codex 会根据 Skill 的描述自动选择它；如需确保本轮
加载，请显式使用 `$mobile-to-harmonyos-porting`。

## 所需输入

- 可读取的上游源项目快照及其访问/授权边界；
- 已存在的 HarmonyOS 目标项目，或创建并冻结最小 Phase 0 目标工程的授权；
- 本次请求的页面与功能分类范围；
- 支持的设备、系统、SDK 与固件；
- 当行为与版本相关时，对应的官方 API、SDK 与协议资料；
- 当验收需要时，测试真实硬件或服务的授权。

## 隐私与安全

不要把 API Key、Token、证书、私有端点、客户数据、专有源代码、生产原始日志、
设备标识、私有协议内容或源项目 UI 素材写入迁移笔记、测试、Issue 或 Pull Request。
请在目标项目中核验源素材的授权与访问边界；这个公开仓库不再分发任何产品素材。

## 验证状态

`v0.1.0` 已完成结构、清单、内容安全与场景覆盖静态校验。独立的新上下文压力场景回放
记录在 [`evals/v0.1.0-results.md`](evals/v0.1.0-results.md)；完成前不得将 Skill 描述为
“已通过行为验证”。

## 许可证

可任选 [MIT](LICENSE-MIT) 或 [Apache-2.0](LICENSE-APACHE) 双许可证。
