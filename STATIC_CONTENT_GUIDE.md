# 静态内容管理指南

本指南说明如何使用新的静态内容管理系统来更新网站内容。

## 概述

网站现在支持两种内容管理模式，可以通过配置文件控制：

1. **静态模式**（推荐）- 内容存储在配置文件和图片文件中，隐藏编辑功能
2. **可编辑模式** - 显示编辑工具栏，支持实时编辑（内容存储在localStorage中）

## 模式配置

在 `js/config.js` 文件的开头，你可以设置网站的运行模式：

```javascript
window.SITE_MODE_CONFIG = {
    // 网站运行模式：'static' 或 'editable'
    mode: 'static',

    // 是否显示工具栏（仅在editable模式下有效）
    showToolbar: true,

    // 是否允许用户切换模式
    allowModeSwitch: true
};
```

### 配置选项说明

- **mode**:
  - `'static'` - 静态模式，页面纯净，无编辑功能
  - `'editable'` - 可编辑模式，显示工具栏和编辑提示

- **showToolbar**:
  - `true` - 在可编辑模式下显示工具栏
  - `false` - 隐藏工具栏

- **allowModeSwitch**:
  - `true` - 允许用户通过工具栏切换模式
  - `false` - 禁止用户切换模式，固定使用配置的模式

## 静态模式的优势

- ✅ **跨设备同步** - 通过Git版本控制实现
- ✅ **无存储限制** - 图片作为静态文件存储
- ✅ **数据持久性** - 不会因浏览器清理而丢失
- ✅ **适合部署** - 完美支持GitHub Pages
- ✅ **团队协作** - 多人可以协作更新内容

## 如何更新内容

### 更新文本内容

1. 打开 `js/text-config.js` 文件
2. 找到 `window.SITE_TEXT_CONFIG` 对象
3. 修改对应的文本内容
4. 保存文件并刷新页面

**示例：**
```javascript
window.SITE_TEXT_CONFIG = {
    'hero-slide-1-title': '如果我们不曾相遇',  // 修改这里
    'hero-slide-1-subtitle': '你又会在哪里',   // 修改这里
    // ... 其他内容
};
```

### 更新图片

#### 方法1: 直接替换图片文件
1. 准备新的图片文件
2. 重命名为对应的文件名（如 `slide-1.jpg`）
3. 替换 `images/` 目录中的对应文件
4. 刷新页面查看效果

#### 方法2: 添加新图片并更新配置
1. 将新图片放入 `images/` 目录的相应子文件夹
2. 打开 `js/config.js` 文件
3. 在 `window.IMAGE_CONFIG` 中更新图片路径
4. 保存文件并刷新页面

**示例：**
```javascript
window.IMAGE_CONFIG = {
    'hero-slide-1-bg': 'images/hero/my-new-image.jpg',  // 更新路径
    // ... 其他图片
};
```

## 图片目录结构

```
images/
├── hero/                   # Hero轮播图背景（3张）
├── beauty/                 # 怎么能这么漂亮区域图片（4张）
├── messages/               # 消息卡片图片（3张）
└── backgrounds/            # 背景图片（统计区域、底部）
```

## 内容键值对照表

### 导航栏
- `nav-brand` - 网站标题
- `nav-home` - 主页链接文字
- `nav-about` - 关于链接文字
- `nav-beauty` - 怎么能这么漂亮链接文字
- `nav-future` - 我眼中的你链接文字
- `nav-message` - 想对你说链接文字

### Hero轮播图（3张）
- `hero-slide-1-title` 到 `hero-slide-3-title` - 主标题
- `hero-slide-1-subtitle` 到 `hero-slide-3-subtitle` - 副标题
- `hero-slide-1-description` 到 `hero-slide-3-description` - 描述文字
- `hero-slide-1-bg` 到 `hero-slide-3-bg` - 背景图片

### 统计数据
- `stat-1-number`, `stat-1-label` - 第1个统计项
- `stat-2-number`, `stat-2-label` - 第2个统计项
- `stat-3-number`, `stat-3-label` - 第3个统计项
- `stat-4-number`, `stat-4-label` - 第4个统计项

### 时间线（6项）
- `timeline-1-year` 到 `timeline-6-year` - 年份
- `timeline-1-content` 到 `timeline-6-content` - 内容描述

### 怎么能这么漂亮（4张图片）
- `beauty-title` - 区域标题
- `beauty-description` - 区域描述
- `beauty-1-caption` 到 `beauty-4-caption` - 图片说明文字
- `beauty-1-image` 到 `beauty-4-image` - 图片文件

### 我眼中的你（6个卡片）
- `future-1-title` 到 `future-6-title` - 卡片标题
- `future-1-content` 到 `future-6-content` - 卡片内容

### 想对你说（3个消息卡片）
- `message-1-content` 到 `message-3-content` - 消息文字
- `message-1-image` 到 `message-3-image` - 消息图片

### 底部信息
- `footer-title-1` 到 `footer-title-3` - 三个栏目的标题
- `footer-content-1` 到 `footer-content-3` - 三个栏目的内容
- `footer-copyright` - 版权信息
- `footer-subtitle` - 底部副标题
- `footer-bg` - 底部背景图片

## 使用编辑模式（可选）

如果你需要使用原有的编辑功能：

1. 点击右下角工具栏中的 "✏️ 编辑模式" 按钮
2. 现在可以双击文本进行编辑，点击图片区域上传图片
3. 编辑完成后，点击 "⚙️ 导出配置" 按钮
4. 下载生成的 `config.js` 文件
5. 用下载的文件替换项目中的 `js/config.js`
6. 点击 "📁 静态模式" 切换回静态模式

## 部署更新

1. 修改完内容后，提交代码到Git仓库：
   ```bash
   git add .
   git commit -m "更新网站内容"
   git push origin main
   ```

2. GitHub Pages会自动重新部署网站

## 注意事项

1. **图片大小**: 建议单张图片不超过2MB，以确保加载速度
2. **图片格式**: 支持JPG、PNG、GIF等常见格式
3. **文本格式**: 支持HTML标签，如 `<br>` 换行标签
4. **备份**: 建议定期备份 `config.js` 文件
5. **测试**: 修改后在本地测试，确认无误后再部署

## 故障排除

### 图片不显示
- 检查图片文件路径是否正确
- 确认图片文件确实存在
- 检查文件名大小写是否匹配

### 文本内容不更新
- 确认修改了正确的键值
- 检查JavaScript语法是否正确
- 清除浏览器缓存后重试

### 配置文件语法错误
- 检查JSON格式是否正确
- 确认所有字符串都用引号包围
- 检查是否有多余的逗号

## 技术支持

如果遇到问题，可以：
1. 检查浏览器控制台的错误信息
2. 参考项目的README.md文件
3. 在GitHub仓库中创建Issue
