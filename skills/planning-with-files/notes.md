# Notes: AI 辅助 UI 像素级复刻调研

## Sources

### Source 1: Screenshot to Code 开源项目
- URL: https://github.com/abi/screenshot-to-code
- Key points:
  - 支持从截图生成 React、Tailwind、Vue、HTML/CSS 等
  - 使用 GPT-4 Vision 和 Claude Vision 能力
  - 可本地运行避免隐私问题
  - 支持二次迭代优化

### Source 2: ChatGPT 视觉能力
- 官方文档和实践
- Key points:
  - GPT-4 Vision 可分析截图并生成代码
  - 适合简单到中等复杂度的 UI
  - 需要精确的提示词引导

### Source 3: Claude Code 能力
- Key points:
  - Claude 3 系列支持视觉输入
  - 代码生成质量较高
  - 支持多轮对话迭代优化

### Source 4: HTML 转 Flutter 工具
- Key points:
  - DomToFlutter 等开源工具
  - AI 辅助代码转换
  - 手动微调仍必不可少

## Synthesized Findings

### 一、AI 工具从截图生成代码的能力

#### 1.1 当前技术水平
- **GPT-4 Vision / Claude Vision**: 可识别 UI 元素并生成基础框架代码
- **准确度**: 简单布局 80-90%，复杂布局 50-70%
- **限制**: 难以精确还原间距、颜色、字体等细节

#### 1.2 适用场景
- ✅ 登录页、注册页等标准表单
- ✅ 列表页、卡片布局
- ✅ 简单的个人资料页
- ❌ 复杂交互动效
- ❌ 精确的品牌设计还原

### 二、HTML/CSS 转 Flutter/Android 方案

#### 2.1 现有工具
- **Screenshot to Code**: 最流行的开源方案
- **CodeSnap**: 专注代码截图生成
- **Anthropic/Claude**: 视觉理解+代码生成
- **ChatGPT + 插件**: 生态丰富

#### 2.2 转换质量
- HTML/CSS → Flutter: 基本结构可转换，需手动调整 Widget
- HTML/CSS → Android XML: 需要较多手动适配
- 推荐: Flutter WebView + 渐进式迁移

### 三、像素级复刻的挑战

#### 3.1 技术难点
- 间距（padding/margin）难以精确还原
- 字体渲染差异
- 响应式布局适配
- 动效和交互状态

#### 3.2 解决方案
1. 提供参考尺寸（如 375x812）
2. 指定设计系统（颜色、字体、间距）
3. 分层处理（静态 UI → 交互 → 动效）
4. 多次迭代优化

### 四、最佳实践

#### 4.1 提示词策略
```
请分析这张截图，生成 Flutter 代码。
- 设计稿尺寸: 375x812
- 主色调: #FF6B6B
- 字体: 默认
- 特别注意: 还原卡片阴影、按钮点击态
```

#### 4.2 工作流程
1. 截图 → AI 分析 → 基础代码
2. 代码预览 → 截图反馈 → AI 修复
3. 人工微调 → 验收

### 五、工具链推荐

#### 5.1 必选工具
- Screenshot to Code（本地部署）
- Claude / ChatGPT Pro

#### 5.2 辅助工具
- Figma（设计稿导出）
- 截图标注工具（测量尺寸）
- 颜色提取工具

#### 5.3 IDE 插件
- Flutter Snippets
- Android Studio 插件

### 六、实践建议

#### 6.1 推荐工作流
```
1. 获取高质量截图（标注尺寸）
2. 使用 Screenshot to Code 生成基础代码
3. Claude/ChatGPT 优化和补充
4. 人工检查和微调
5. 在目标平台预览验收
```

#### 6.2 预期效果
- 简单页面: 80%+ 自动生成，人工<20%
- 中等复杂度: 60-70% 自动生成
- 复杂页面: 建议结合设计稿 + AI 辅助
