# Spec Driven Creation (SDC)

规格驱动创作：将软件工程中的规格驱动开发（SDD）和行为驱动开发（BDD）思想迁移到内容创作领域。

先定义Spec（创作需求与验收标准），再按Spec创作，最后用Harness（检查清单）逐项验收，不通过不交付。

---

## 核心理念

**Spec是唯一真相源。** 创作前先写Spec，定义"做什么"和"验收标准"；创作中按Spec执行；创作后对照Spec和Harness验收。

| SDC概念 | 对应工程概念 | 说明 |
|---------|----------------|------|
| Spec | Creative Brief / Requirements | 创作需求文档，定义做什么和验收标准 |
| Harness | Definition of Done / Code Review | 验收检查清单，逐项验证 |
| Cycle Log | Retrospective / Post-mortem | 复盘日志，驱动持续改进 |

---

## 架构：框架与配置分离

本仓库提供**通用框架**（方法论 + 空模板）。项目私有的配置（创作风格、人设库、合规规则等）在使用时于项目目录（cwd）的 `.sdc/` 中生成和管理，不进入本仓库。

```
你的项目目录/
├── .sdc/                      # 项目私有配置（不公开）
│   ├── creative-style.md      # 创作风格规范
│   ├── personas.md            # 视角/角色库
│   ├── compliance.md          # 合规规则
│   ├── citation.md            # 引用与数据规范
│   └── harness-checklist.md   # 填充好的Harness检查项
├── spec.md                    # 当前Spec（从模板复制）
├── draft.md                   # 初稿
├── harness-report.md          # Harness审查报告
└── cycle-log.md               # 复盘日志
```

---

## 快速开始

### 1. 初始化项目

在你的项目目录中：
1. 复制 `templates/` 下的空模板到项目目录
2. 创建 `.sdc/` 目录，编写项目私有配置
3. 填写 `spec.md`，定义创作需求和验收标准

### 2. SDC六步创作流程

1. **Spec定义** → 填写 `spec.md`
2. **素材准备** → 收集引用、查证数据
3. **初稿撰写** → 按Spec撰写，加载 `.sdc/` 配置
4. **Harness审查** → 逐项验证，生成 `harness-report.md`
5. **修改复审** → 修复不通过项，重跑Harness
6. **交付归档** → 终稿 + 参考资料 + 复盘 `cycle-log.md`

详细SOP见 [sop.md](sop.md)。

---

## 文件结构

```
spec-driven-creation/
├── SKILL.md                    # Skill入口与使用指南
├── sop.md                      # SDC六阶段创作流程 + 自更新机制
├── templates/                  # 空模板（复制到项目目录使用）
│   ├── spec-template.md        # Spec定义模板
│   ├── harness-template.md     # Harness检查清单模板
│   └── cycle-log-template.md   # 创作周期复盘模板
├── LICENSE                     # MIT
└── README.md                   # 本文件
```

---

## 适用领域

- 文章 / 散文 / 随笔
- 视频脚本 / 短视频文案
- 哲学对话 / 访谈稿
- 朋友圈长文案 / 社交媒体内容
- 技术文档 / 教程
- 任何需要规范化、可验证创作流程的叙事性文本

---

## 自更新机制

每个创作周期用Cycle Log复盘，发现框架不足就主动更新：
- **通用框架更新**（sop.md、templates/、SKILL.md）→ 提交到本仓库
- **项目配置更新**（.sdc/）→ 在项目目录中更新，不影响本仓库

详见 [sop.md](sop.md) 自更新机制章节。

---

## License

MIT
