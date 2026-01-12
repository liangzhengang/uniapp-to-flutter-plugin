---
name: uniapp-ui-extractor
description: 提取指定路径 uniapp 页面 UI 转成 YAML 数据
context: fork
agent: extractor-agent
---
# 核心原则
**GOAL**: 像素级复刻 uniapp 页面 UI，页面相似度要求 95%
**MUST** 图片资源必须复制 
**页面结构** 
- 页面结构层（Page Layout Tree）
- 视觉组件层（Visual Components）
- 业务组件层（仅标注，不展开）
**FORBIDDEN**
- 不允许合并组件
- 不允许推测缺失样式

---

## 页面结构分析
- 源页面组件层次结构
- 自定义组件结构 
- 关键尺码对照表
- 字体大小对照表
- 圆角对照表

---

## 颜色定义
- 颜色常量
- 颜色使用对照表
- 颜色仅按源码与运行态提取
- 不允许合并相近颜色 (重要)

---

## 图片资源清单 (重要)
- 列出图片用途
- **必须**复制图片到Flutter 项目中assets/images/

---

# OUTPUT GUIDANCES
**GOAL** 以 YAML 输出分析结果

----

# few-shot
```Prompt:
   请从 Uniapp 页面文件中提取完整的 UI 结构和数据:

       源文件路径: /Volumes/codePlace/senssunGit/smartlink-harmony-uni/src/pages/baby/index/components/measure/measure.vue

       输出要求:
       1. 完整的页面结构树（所有组件层级关系）
       2. 所有自定义组件清单（包括嵌套组件）
       3. 所有样式属性（尺寸、颜色、间距、圆角等）
       4. 所有图片资源路径
       5. 所有文本内容和国际化key
       6. 所有交互元素（按钮、输入框等）
       7. 动态数据绑定点

       输出格式: 将提取的 UI 数据保存为 YAML 文件到: /Volumes/codePlace/localCode/00_ACTIVE/smartlink_flutter/conversion/measure/ui_yaml/

       请生成以下文件:
       - page_structure.yaml - 页面完整结构
       - components_list.yaml - 组件清单
       - styles_inventory.yaml - 样式清单
       - assets_inventory.yaml - 资源文件清单
       - data_bindings.yaml - 数据绑定点

       请确保提取完整且准确，不要遗漏任何细节。
```



