# Medical Skill Finder

从 [OpenClaw-Medical-Skills](https://github.com/FreedomIntelligence/OpenClaw-Medical-Skills) 医疗技能库中搜索所需技能。

[English](#english) | [中文](#中文)

---

## 中文

### 功能

- 📥 自动同步最新技能库（870+ 医疗 AI 技能）
- 🔍 关键词精准匹配
- 🌐 支持中文/英文双语
- 📋 返回安装命令和 GitHub 链接

### 安装

```bash
# 复制到 OpenClaw skills 目录
cp -r ~/clawd/skills/medical-skill-finder ~/.openclaw/skills/
```

### 快速开始

```bash
# 首次使用先同步技能库
medical-skill-finder sync          # 中文版
medical-skill-finder sync-en       # English

# 搜索想要的技能
medical-skill-finder search "PubMed"
medical-skill-finder search "药物发现" 10

# 查看详情
medical-skill-finder show biomedical-search

# 按分类浏览
medical-skill-finder list "医疗专用工具"
medical-skill-finder list "生物信息学"

# 统计信息
medical-skill-finder stats
```

### 命令详解

| 命令 | 说明 |
|------|------|
| `sync` | 同步技能库（默认中文） |
| `sync-zh` | 同步中文技能库 |
| `sync-en` | 同步英文技能库 |
| `search <关键词> [数量]` | 搜索技能 |
| `show <技能名>` | 显示技能详情 |
| `list [分类]` | 列出所有技能或指定分类 |
| `stats` | 显示统计信息 |

### 常见搜索场景

| 场景 | 搜索关键词 |
|------|-----------|
| 文献检索 | PubMed, biomedical, literature |
| 临床试验 | ClinicalTrials, 临床试验 |
| 药物研究 | drug discovery, 药物发现 |
| 基因分析 | 基因组, genome, GWAS |
| 蛋白质 | AlphaFold, protein structure |
| 医疗器械 | FDA, 医疗器械, regulation |
| 单细胞分析 | single-cell, scRNA-seq |

### 输出示例

```
🔍 搜索: PubMed

找到 1 个相关技能:

📦 pubmed-search
   描述: 搜索 PubMed 科学文献。当用户要求查找论文、搜索文献、查询研究、查找出版物或询问近期研究时触发。
   分类: 医疗专用工具
   🔗 https://github.com/.../skills/pubmed-search
   安装: cp -r ~/.openclaw/skills-repo/skills/pubmed-search ~/.openclaw/skills/
```

---

## English

### Features

- 📥 Auto-sync latest skill library (870+ medical AI skills)
- 🔍 Precise keyword matching
- 🌐 Bilingual support (Chinese/English)
- 📋 Install commands and GitHub links included

### Installation

```bash
# Copy to OpenClaw skills directory
cp -r ~/clawd/skills/medical-skill-finder ~/.openclaw/skills/
```

### Quick Start

```bash
# First time: sync the skill library
medical-skill-finder sync          # Chinese
medical-skill-finder sync-en       # English

# Search for skills
medical-skill-finder search "PubMed"
medical-skill-finder search "drug discovery" 10

# Show details
medical-skill-finder show biomedical-search

# Browse by category
medical-skill-finder list "Medical Tools"
medical-skill-finder list "Drug Discovery & Design"

# Statistics
medical-skill-finder stats
```

### Commands

| Command | Description |
|---------|-------------|
| `sync` | Sync skill library (default Chinese) |
| `sync-zh` | Sync Chinese skill library |
| `sync-en` | Sync English skill library |
| `search <query> [limit]` | Search skills |
| `show <skill-name>` | Show skill details |
| `list [category]` | List all skills or by category |
| `stats` | Show statistics |

### Common Search Cases

| Use Case | Keywords |
|----------|----------|
| Literature Search | PubMed, biomedical, literature |
| Clinical Trials | ClinicalTrials, clinical trials |
| Drug Discovery | drug discovery, molecule |
| Genomics | genome, GWAS, variant |
| Protein | AlphaFold, protein structure |
| Medical Device | FDA, regulation, certification |
| Single Cell | single-cell, scRNA-seq |

### Output Example

```
🔍 Searching: PubMed

Found 1 related skills:

📦 pubmed-search
   Description: Search PubMed for scientific literature. Use when the user asks to find papers...
   Category: Medical Tools
   🔗 https://github.com/.../skills/pubmed-search
   Install: cp -r ~/.openclaw/skills-repo/skills/pubmed-search ~/.openclaw/skills/
```

---

## 技能分类 (Categories)

### 科学数据库 (Scientific Databases)

- 科学数据库（基因组与变异）
- 科学数据库（蛋白质、通路与药物）
- Scientific Databases (Genomics & Variants)
- Scientific Databases (Proteins, Pathways & Drugs)

### 生物信息学 (Bioinformatics)

- 生物信息 — 测序与读长质控
- 生物信息 — 临床数据库与变异分析
- 生物信息 — 差异表达与转录组学
- 生物信息 — 通路与网络分析
- 生物信息 — 单细胞与空间组学
- 生物信息 — 表观基因组学与染色质

### 药物与分子 (Drug & Molecule)

- 药物安全与化学生物学
- 化学信息学与药物发现
- 药物发现与分子设计
- Drug Discovery & Design

### 蛋白质 (Protein)

- 蛋白质结构与设计
- 蛋白质组学与质谱
- Protein Structure & Design

### 医学 (Medical)

- 医疗专用工具
- 医学影像与病理
- 医疗 ML 与临床 AI
- Medical Tools
- Medical Imaging & Pathology
- Healthcare ML & Clinical AI

---

## 技术细节

- 索引数据保存在 `~/.openclaw/medical-skills-index.json`
- 从 GitHub README 解析技能列表和分类
- 自动检测当前语言设置

### 重新构建索引

```bash
rm ~/.openclaw/medical-skills-index.json
medical-skill-finder sync
```

---