---
name: spec-driven-creation
description: SDC（Spec Driven Creation，规格驱动创作）完整方法论与模板集。将软件工程中的规格驱动开发（SDD）和行为驱动开发（BDD）思想迁移到内容创作领域：先定义Spec（创作需求与验收标准），再按Spec创作，最后用Harness（检查清单）逐项验收，不通过不交付。适用于文章、视频脚本、散文、对话、文案等任何叙事性文本的规范化创作。使用场景：(1) 需要可重复、可验证、可追溯的内容创作流程；(2) 需要在创作前明确需求和验收标准；(3) 需要用检查清单替代主观判断进行质量验收；(4) 需要通过复盘持续改进创作流程；(5) 需要在项目目录中管理创作风格、人设库、合规规则等项目私有配置。核心交付：SDC六阶段SOP、Spec模板、Harness检查清单模板、Cycle Log复盘模板、项目配置初始化指南。
---

# Spec Driven Creation (SDC)

规格驱动创作：先定Spec再创作，创作完用Harness验收，不通过不交付。

本Skill是一个完整、自包含的SDC创作框架，包含通用方法论和空模板。**项目私有的配置（创作风格、人设库、合规规则、填充好的检查项等）不在Skill中，而是在使用Skill时在项目目录（cwd）中生成和管理。**

---

## 核心理念

**Spec是唯一真相源（Single Source of Truth）。** 创作前先写Spec，定义"做什么"和"验收标准"；创作中按Spec执行；创作后对照Spec和Harness验收。不通过不交付。

**三个等价关系：**
- Spec ≈ Creative Brief / Content Brief（创作需求文档）
- Harness ≈ Definition of Done + Editorial Review（验收检查清单）
- Cycle Log ≈ Retrospective / Post-mortem（复盘日志，驱动自更新）

**与传统创作的区别：**
- 传统：想到什么写什么，写完凭感觉判断好不好
- SDC：先定义需求和验收标准，写完对照清单逐项验证，可重复、可追溯、可迭代

---

## 架构：Skill + 项目配置（cwd）

本Skill采用**框架与配置分离**的架构：

| 层 | 位置 | 内容 | 说明 |
|----|------|------|------|
| 通用框架 | Skill内置 | SDC方法论 + 空模板 | 开源、共享、所有项目通用 |
| 项目配置 | 项目目录（cwd） | 创作风格、人设库、合规规则、引用规范、填充好的Harness检查项 | 私有、每个项目独立、在cwd中生成和管理 |

**工作方式：**
1. 在项目目录（cwd）中初始化SDC项目配置
2. 创作时，Skill的通用方法论 + cwd中的项目配置 结合使用
3. 所有创作产物（Spec、初稿、Harness报告、终稿）都保存在cwd中
4. 项目配置可以在不同项目间复用，也可以每个项目独立定制

---

## 快速开始

### 第一步：在cwd初始化项目配置

在你的项目目录中，创建SDC项目配置结构：

```
你的项目目录/
├── .sdc/                      # SDC项目配置（私有，不提交到公开仓库）
│   ├── creative-style.md      # 创作风格规范
│   ├── personas.md            # 专家人设库
│   ├── compliance.md          # 合规规则（脱敏/内容边界/版权）
│   ├── citation.md            # 引用与数据规范
│   └── harness-checklist.md   # 填充好的Harness具体检查项
├── spec.md                    # 当前项目的Spec（从模板复制填写）
├── draft.md                   # 初稿
├── harness-report.md          # Harness审查报告
└── cycle-log.md               # 创作周期复盘日志
```

**初始化方式：**
1. 从Skill的 `templates/` 目录复制空模板到cwd：
   - `templates/spec-template.md` → `spec.md`
   - `templates/harness-template.md` → `harness-report.md`（或 `.sdc/harness-checklist.md`）
   - `templates/cycle-log-template.md` → `cycle-log.md`
2. 创建 `.sdc/` 目录，编写项目私有配置文件（创作风格、人设库、合规规则等）
3. 如果已有项目配置，直接复用

> 项目配置文件（`.sdc/`下的内容）是每个项目私有的，不应提交到公开仓库。建议在项目的`.gitignore`中添加 `.sdc/`。

### 第二步：SDC六步创作流程

1. **Spec定义**：在cwd中填写 `spec.md`，定义创作需求和验收标准
2. **素材准备**：收集引用资料、查证数据、规划素材
3. **初稿撰写**：按Spec撰写 `draft.md`，加载 `.sdc/` 中的项目配置（创作风格、人设库、合规规则等）
4. **Harness审查**：使用 `.sdc/harness-checklist.md`（从模板填充）逐项验证，生成 `harness-report.md`
5. **修改复审**：修复不通过项，重跑Harness直到通过
6. **交付归档**：终稿 + 参考资料 + Spec + Harness报告，填写 `cycle-log.md` 复盘

完整SOP见 [sop.md](sop.md)。

---

## 核心原则

| 原则 | 说明 |
|------|------|
| Spec先行 | 不写无Spec的内容，创作前必须明确需求和验收标准 |
| Harness验收 | 创作完成后必须跑检查清单，阻断级问题不修复不交付 |
| 可追溯 | Spec、初稿、Harness报告、终稿全部归档在cwd，可追溯每一步 |
| 可重复 | 流程标准化，不同创作者按同一流程产出质量一致的内容 |
| 自更新 | 每个创作周期用Cycle Log复盘，发现框架不足就主动更新 |
| 框架配置分离 | 通用框架（Skill）与项目配置（cwd）解耦，框架可开源，配置可私有 |

---

## 文件结构

```
spec-driven-creation/          # Skill本身（开源、通用）
├── SKILL.md                    # 本文件，入口与使用指南
├── sop.md                      # SDC六阶段创作流程 + 自更新机制
├── templates/                  # 空模板（复制到cwd使用）
│   ├── spec-template.md        # Spec定义模板
│   ├── harness-template.md     # Harness检查清单模板（空结构）
│   └── cycle-log-template.md   # 创作周期复盘模板
├── LICENSE                     # 开源协议（MIT）
├── README.md                   # 项目说明
└── .gitignore                  # 忽略项目私有配置
```

### cwd中的项目配置（使用时生成）

```
你的项目目录/
├── .sdc/                      # 项目私有配置（不公开）
│   ├── creative-style.md      # 创作风格规范
│   ├── personas.md            # 专家人设库
│   ├── compliance.md          # 合规规则
│   ├── citation.md            # 引用与数据规范
│   └── harness-checklist.md   # 填充好的Harness检查项
├── spec.md                    # 当前Spec
├── draft.md                   # 初稿
├── harness-report.md          # Harness审查报告
└── cycle-log.md               # 复盘日志
```

---

## 项目配置编写指南

`.sdc/` 目录下的配置文件是每个项目私有的，以下是编写建议：

### creative-style.md（创作风格）
定义项目的语言风格、情绪基调、结构逻辑、禁忌清单等。参考维度：
- 角色定位（谁在说话，对谁说话）
- 语言风格（用词、句式、对话感、人称）
- 情绪基调（底色、活泼/沉重比例、特殊主题）
- 结构逻辑（开场、主体、结尾的规范）
- 禁忌清单（绝对不能出现的内容/表达方式）

### personas.md（人设库）
定义创作中可调用的专家人设。每个人设包含：
- 触发场景（什么时候用这个人设）
- 核心视角（这个人设的分析角度）
- 语言风格（这个人设的说话方式）
- 常用概念（这个人设的专业术语）
- 边界（这个人设不能做什么）

### compliance.md（合规规则）
定义项目的合规要求：
- 脱敏规则（哪些个人信息不能出现，如何模糊化）
- 内容边界（政治/经济/敏感内容的处理原则）
- 版权规范（素材使用、引用标注的规则）

### citation.md（引用规范）
定义引用和数据的标注规则：
- 引用标注格式
- 数据查证要求
- 参考资料列表格式

### harness-checklist.md（Harness检查项）
从 `templates/harness-template.md` 复制，填充项目具体的检查项。每个检查项包含：
- 检查内容
- 通过标准
- 严重程度（阻断/重要/建议）

---

## 自更新机制

创作过程中发现框架不足（模板字段不够用、Harness缺检查项、SOP步骤有问题等），主动更新并记录变更。

**更新范围：**
- Skill通用框架（sop.md、templates/）的更新 → 提交到本仓库
- 项目私有配置（.sdc/）的更新 → 在项目目录中更新，不影响Skill

**更新原则：** 小步快跑、向后兼容、记录原因、版本可追溯。

详见 [sop.md](sop.md) 自更新机制章节。

---

## 适用领域

SDC方法论不限于特定创作类型，适用于：
- 文章 / 散文 / 随笔
- 视频脚本 / 短视频文案
- 哲学对话 / 访谈稿
- 朋友圈长文案 / 社交媒体内容
- 技术文档 / 教程
- 任何需要规范化、可验证创作流程的叙事性文本
