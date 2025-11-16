# Advanced Commenter Levels

WordPress 评论者等级插件，自动为评论用户添加等级徽章标识。

## 功能特性

- **自动等级计算**: 基于评论数量自动计算用户等级
- **5+1 等级体系**: VIP1-VIP5 五个等级 + 博主特殊等级
- **手动覆盖**: 支持在后台手动指定用户等级
- **自定义样式**: 可自定义等级标签文字和背景颜色

## 等级规则

| 等级 | 评论数阈值 | 默认标签 | 默认颜色 |
| ---- | ---------- | -------- | -------- |
| 博主 | 管理员     | 博主     | #7db9de  |
| VIP1 | 2+         | V1       | #F3F4F7  |
| VIP2 | 5+         | V2       | #E7E8EF  |
| VIP3 | 10+        | V3       | #B3CEDE  |
| VIP4 | 25+        | V4       | #95BCD3  |
| VIP5 | 50+        | V5       | #D97967  |

## 安装方法

1. 下载插件并上传到 `/wp-content/plugins/` 目录
2. 在 WordPress 后台插件列表启用 "Advanced Commenter Levels"
3. 访问 "设置" → "评论等级" 配置插件

## 配置说明

### 等级样式设置

- 进入设置页面自定义每个等级的显示标签和背景颜色
- 支持颜色选择器，实时预览颜色效果

### 评论者等级管理

- 查看所有评论者列表及其评论统计
- 手动覆盖自动计算的等级
- 搜索特定邮箱地址的评论者

## 技术要求

- WordPress 5.0+
- PHP 7.2+

## 技术架构

```
includes/
├── class-acl-core.php              # 核心功能
├── class-acl-db.php                # 数据库操作
├── class-acl-caching.php           # 缓存管理
├── class-acl-defaults.php          # 默认配置
└── class-acl-admin-merged.php      # 后台管理

assets/
├── css/acl-frontend.css           # 前端样式
├── css/acl-admin.css              # 后台样式
├── js/acl-frontend.js             # 前端脚本
└── js/acl-admin-*.js              # 后台脚本
```

## 开发说明

### 钩子过滤器

```php
// 获取用户等级数据
$level_data = $core->get_level_data($user_id, $email);
```

### 过滤器

- `get_comment_author_link` - 用于在评论作者链接后添加等级徽章

## 缓存机制

插件使用 WordPress transients API 缓存评论数，默认缓存时间 2 小时，在以下情况自动清除缓存：

- 发布新评论
- 编辑评论
- 删除评论
- 手动设置等级覆盖

## 浏览器兼容性

- ✅ Chrome/Edge (Blink)
- ✅ Firefox (Gecko)
- ✅ Safari (WebKit)

## 贡献

欢迎提交 Issue 和 Pull Request！

## License

GPL v2 or later
