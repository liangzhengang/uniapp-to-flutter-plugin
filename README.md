# UniApp 到 Flutter 转换器

Claude Code 插件 - 将 UniApp 页面转换为 Flutter 页面的完整工作流。

## 功能特性

- **UI 提取**：从 UniApp 页面提取完整的 UI 结构和数据（YAML 格式）
- **组件转换**：将 UniApp 自定义组件转换为 Flutter 自定义组件
- **像素级评审**：基于原始 UI 数据进行像素级精度评审
- **多方案生成**：支持生成多种实现方案并评估选择最佳方案

## 安装方式

### 本地安装

```bash
cd /path/to/unipp-to-flutter-plugin
claude plugin install .
```

### 从 GitHub 安装

```bash
claude plugin install gh:yourusername/unipp-to-flutter-plugin
```

## 使用方法

### 命令

```bash
/uniapp-to-flutter <page_path>
```

**示例：**
```bash
/uniapp-to-flutter baby/index
```

这将启动完整的工作流：
1. **Discovery**：验证页面路径，识别项目结构
2. **Extraction**：提取 UI 数据为 YAML
3. **Component Analysis**：分析自定义组件
4. **Review & Architect**：评审并选择最佳方案
5. **Implementation**：生成 Flutter 代码
6. **Summary**：输出转换报告

### Skills

使用 `uniapp-ui-extractor` skill 单独提取 UI 数据：

```
请从 UniApp 页面文件中提取完整的 UI 结构和数据:
源文件路径: /path/to/page.vue
输出路径: /path/to/output/
```

### Agents

- **extractor-agent**：提取 UI 数据
- **flutter-Component-agent**：转换自定义组件
- **flutter-ui-reviewer**：评审 UI 还原度
- **widget-builder**：Vue 转 Flutter + Riverpod

## 项目结构

```
unipp-to-flutter-plugin/
├── .claude-plugin/
│   └── plugin.json           # 插件配置
├── commands/
│   └── uniapp-to-flutter.md  # 命令定义
├── skills/
│   └── uniapp-ui-extractor/
│       └── SKILL.md          # Skill 定义
├── agents/
│   ├── extractor-agent.md
│   ├── flutter-Component-agent.md
│   ├── flutter-ui-reviewer.md
│   └── widget-builder.md
└── README.md
```

## 输出目录结构

转换后的文件将保存在 Flutter 项目的 `conversion/{page}/` 目录下：

```
conversion/{page}/
├── ui_yaml/                  # 原始 UI 数据
│   ├── L0_history_index.yaml
│   ├── L1_Structure_Layer.yaml
│   ├── L2_Component_Layer.yaml
│   ├── L4_Visual_Layer.yaml
│   ├── L5_Interaction_Layer.yaml
│   └── assets_inventory.yaml
├── blueprints/               # 架构蓝图
├── lib/src/pages/{page}.dart # 生成的 Flutter 页面
└── {page}-component-mapping.md
```

## 要求

- UniApp 项目源文件
- Flutter 项目目标目录
- Claude Code CLI

## 更新插件

```bash
claude plugin update uniapp-to-flutter
```
