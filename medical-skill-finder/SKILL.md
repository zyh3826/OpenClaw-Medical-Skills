---
name: medical-skill-finder
description: 从 OpenClaw-Medical-Skills 医疗技能库（872+ skills）中搜索匹配的技能。支持关键词搜索和语义搜索，返回技能名称、描述、分类、GitHub 链接和安装命令。
keywords:
  - medical-skills
  - skill-search
  - healthcare
  - biomedical
  - clinical
allowed-tools: Bash(medical-skill-finder:*)
---

# Medical Skill Finder

从 [OpenClaw-Medical-Skills](https://github.com/FreedomIntelligence/OpenClaw-Medical-Skills) 医疗技能库中搜索所需技能。

## 功能

- 📥 自动同步最新技能库（872+ 医疗 AI 技能）
- 🔍 关键词精准匹配
- 🧠 语义搜索（自然语言描述需求）
- 📋 返回安装命令和 GitHub 链接

## 快速开始

```bash
# 首次使用先同步技能库
medical-skill-finder sync

# 搜索想要的技能
medical-skill-finder search "PubMed 文献搜索"
medical-skill-finder search "药物相互作用预测"
medical-skill-finder search "基因变异注释"
medical-skill-finder search "临床试验数据库"
medical-skill-finder search "蛋白质结构预测"
```

## 命令详解

### 1. 同步技能库

```bash
medical-skill-finder sync
```

首次使用或需要更新技能库时运行。它会：
- 克隆/更新 OpenClaw-Medical-Skills 仓库
- 解析所有 SKILL.md 文件
- 构建本地索引供快速搜索

### 2. 搜索技能

```bash
medical-skill-finder search <关键词或描述>
```

**参数：**
- `关键词或描述`：你想做什么（如 "文献搜索"、"药物发现"、"基因分析"）

**示例：**
```bash
# 基础搜索
medical-skill-finder search "PubMed"

# 语义搜索 - 描述你的需求
medical-skill-finder search "我想查最新的临床试验"
medical-skill-finder search "分析蛋白质结构"
medical-skill-finder search "药物副作用监测"

# 指定返回数量
medical-skill-finder search "癌症基因组" 10
```

### 3. 查看技能详情

```bash
medical-skill-finder show <skill名称>
```

查看某个技能的完整信息，包括：
- 详细描述
- 关键词
- GitHub 链接
- 安装命令

### 4. 列出所有技能

```bash
# 按分类列出
medical-skill-finder list

# 列出特定分类的技能
medical-skill-finder list "生物信息学"
medical-skill-finder list "药物发现"
medical-skill-finder list "临床医学"

# 列出包含特定关键词的技能
medical-skill-finder list --keyword "RNA"
medical-skill-finder list --keyword "癌症"
```

### 5. 分类统计

```bash
medical-skill-finder stats
```

查看技能库的统计信息：
- 总技能数
- 各分类数量
- 热门关键词

## 常见搜索场景

| 场景 | 搜索关键词 |
|------|-----------|
| 文献检索 | PubMed, bioRxiv, 论文, 文献 |
| 临床试验 | ClinicalTrials, 临床试验, 试验查询 |
| 药物研究 | 药物发现, DDI, ADMET, 药物警戒 |
| 基因分析 | 基因组, 变异, GWAS, VCF |
| 蛋白质 | AlphaFold, 蛋白质结构, 抗体设计 |
| 医疗器械 | FDA, IEC 62304, 法规, 认证 |
| 临床报告 | SOAP, 出院小结, 病历 |
| 医学影像 | 影像, 病理, CT, MRI |

## 输出示例

```
🔍 搜索 "药物相互作用预测"

找到 5 个相关技能:

1. drug-drug-interaction-prediction
   描述: Drug-drug interaction prediction using transformer models
   关键词: DDI, 药物相互作用, 药物安全
   分类: 药物安全与化学生物学
   🔗 https://github.com/MedClaw-Org/OpenClaw-Medical-Skills/tree/main/skills/drug-drug-interaction-prediction
   
2. pharmacovigilance
   描述: Pharmacovigilance and adverse drug reaction monitoring
   关键词: 药物警戒, ADR, 药物安全
   分类: 药物安全与化学生物学
   ...

安装命令:
  cp -r ~/.openclaw/skills-repo/skills/drug-drug-interaction-prediction ~/.openclaw/skills/
```

## 工作原理

1. **同步阶段**: 克隆 GitHub 仓库，解析所有 SKILL.md
2. **索引阶段**: 提取 name, description, keywords, category
3. **搜索阶段**: 
   - 关键词模式：精确匹配 name/description/keywords
   - 语义模式：使用模糊匹配和相关性排序

## 配置文件

索引数据保存在 `~/.openclaw/medical-skills-index.json`

如需重新构建索引，删除后运行 `sync`：
```bash
rm ~/.openclaw/medical-skills-index.json
medical-skill-finder sync
```
