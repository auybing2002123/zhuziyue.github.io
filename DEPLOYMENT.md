# 部署指南

本文档详细说明如何将项目部署到GitHub Pages。

## 快速部署步骤

### 1. 准备GitHub仓库

1. 在GitHub上创建一个新仓库
2. 将项目代码上传到仓库
3. 确保仓库是公开的（GitHub Pages免费版需要公开仓库）

### 2. 配置GitHub Pages

1. 进入仓库的 **Settings** 页面
2. 滚动到 **Pages** 部分
3. 在 **Source** 下选择 **GitHub Actions**
4. 系统会自动检测到 `.github/workflows/deploy.yml` 文件

### 3. 更新配置文件

编辑以下文件中的配置：

#### `_config.yml`
```yaml
url: "https://你的用户名.github.io"
baseurl: "/你的仓库名"
```

#### `package.json`
```json
{
  "repository": {
    "url": "https://github.com/你的用户名/你的仓库名.git"
  },
  "homepage": "https://你的用户名.github.io/你的仓库名"
}
```

#### `index.html`
更新meta标签中的URL：
```html
<meta property="og:url" content="https://你的用户名.github.io/你的仓库名/">
<meta property="twitter:url" content="https://你的用户名.github.io/你的仓库名/">
```

### 4. 推送代码

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 5. 等待部署

- GitHub Actions会自动开始构建和部署
- 在仓库的 **Actions** 标签页可以查看部署进度
- 部署完成后，网站将在 `https://你的用户名.github.io/你的仓库名` 可访问

## 自定义域名（可选）

如果你有自己的域名：

1. 在仓库根目录创建 `CNAME` 文件
2. 在文件中写入你的域名，如：`www.yourdomain.com`
3. 在域名提供商处配置DNS记录指向GitHub Pages

## 故障排除

### 部署失败
- 检查 `.github/workflows/deploy.yml` 文件是否正确
- 确保仓库是公开的
- 查看Actions日志了解具体错误

### 页面无法访问
- 确认GitHub Pages已启用
- 检查URL是否正确
- 等待DNS传播（可能需要几分钟）

### 样式或脚本无法加载
- 检查文件路径是否正确
- 确认 `baseurl` 配置是否正确
- 使用相对路径而不是绝对路径

## 本地开发

在本地测试网站：

```bash
# 安装依赖
npm install

# 启动本地服务器
npm start

# 或者使用Python
python -m http.server 8080

# 或者使用Node.js
npx http-server . -p 8080
```

## 更新网站

1. 修改代码
2. 提交并推送到GitHub
3. GitHub Actions会自动重新部署

## 性能优化建议

1. **图片优化**：压缩图片文件大小
2. **缓存设置**：利用浏览器缓存
3. **CDN加速**：使用CDN加速静态资源
4. **代码压缩**：压缩CSS和JavaScript文件

## 安全注意事项

1. 不要在代码中包含敏感信息
2. 定期更新依赖包
3. 使用HTTPS（GitHub Pages默认支持）
4. 考虑添加Content Security Policy

## 监控和分析

可以添加以下服务来监控网站：

- **Google Analytics**：网站访问统计
- **Google Search Console**：搜索引擎优化
- **Uptime监控**：网站可用性监控

## 备份策略

1. 定期导出网站内容
2. 保存重要的用户数据
3. 备份仓库到其他平台

## 支持

如果遇到问题：

1. 查看GitHub Pages文档
2. 检查GitHub Status页面
3. 在仓库中创建Issue
4. 联系GitHub支持
