# 沉香产品销售独立站 - 研发规范

## 应用概览

沉香产品展示与销售独立站，东方禅意美学风格。前台支持多语言展示，后台提供完整的产品与内容管理能力。

### 语言支持
- 中文 (zh) - 默认
- 英文 (en)
- 阿拉伯语 (ar) - RTL 布局
- 泰语 (th)
- 马来语 (ms)

## 设计规范

### 色彩系统（东方禅意 · 深木色+金色）

| Token | 值 | 用途 |
|-------|-----|------|
| `--primary` | `hsl(35 65% 28%)` | 深木色主色，导航/按钮/标题 |
| `--primary-foreground` | `hsl(40 30% 94%)` | 主色上的文字（米白） |
| `--accent` / `--gold` | `hsl(42 70% 55%)` | 金色点缀，高亮/价格/装饰线 |
| `--accent-foreground` | `hsl(35 65% 18%)` | 金色上的文字（深木色） |
| `--background` | `hsl(40 25% 96%)` | 米白底，宣纸质感 |
| `--foreground` | `hsl(30 15% 20%)` | 正文深棕 |
| `--muted-foreground` | `hsl(30 8% 45%)` | 次要文字 |
| `--card` | `hsl(0 0% 100%)` | 卡片底 |
| `--border` | `hsl(35 20% 85%)` | 浅木色边框 |
| `--incense-dark` | `hsl(30 40% 15%)` | 沉香黑，页脚/深背景 |
| `--incense-light` | `hsl(35 40% 88%)` | 浅木色，装饰底纹 |

### 排版

- 字体栈：`"Noto Serif SC", "Songti SC", "Source Han Serif SC", Georgia, serif`（标题衬线，东方韵味）
- 正文：`system-ui, "PingFang SC", "Microsoft Yahei", sans-serif`
- 标题字号层级：48 / 36 / 28 / 22 / 18 px（桌面端）
- 行高：标题 1.3，正文 1.75
- 字间距：标题 +0.05em

### 间距
- 内容最大宽度：1200px
- 区块内边距：桌面 `py-20 px-6`，移动 `py-12 px-4`
- 卡片间距：`gap-6`（网格）/ `gap-4`（列表）

### 设计语言
- 大量留白，疏密有致
- 细金线分隔（1px solid --accent/30）
- 竖向排版元素点缀（竖排文字、竖线分隔）
- 宣纸纹理背景（浅米底 + 微妙噪点）
- 过渡动效：缓慢优雅，300ms ease-out

## 信息架构

### 前台路由
- `/` - 首页（Hero + 分类 + 荣誉 + 热门 + 工艺 + CTA）
- `/products` - 产品列表（分类筛选）
- `/products/:id` - 产品详情
- `/about` - 关于我们（品牌故事）
- `/contact` - 联系我们（表单+信息）

### 后台路由
- `/admin/login` - 管理员登录
- `/admin/dashboard` - 后台首页
- `/admin/products` - 产品管理
- `/admin/categories` - 分类管理
- `/admin/content` - 网站内容管理
- `/admin/inquiries` - 询盘管理

## 数据模型

### 核心表
- `products` - 产品（多语言名称/描述）
- `categories` - 产品分类（多语言名称）
- `site_content` - 网站内容配置（JSON 结构，多语言）
- `inquiries` - 询盘记录
- `admins` - 管理员账号

### 多语言字段约定
所有多语言字段使用 JSONB 存储，key 为语言 code：
```json
{ "zh": "沉香", "en": "Agarwood", "ar": "...", "th": "...", "ms": "..." }
```

## 前后端约定

- 所有前台公开接口无需登录，后台接口需 admin token
- 图片上传走 dataloom 前端上传，后端存 URL
- 产品分类：线香(incense-stick) / 沉香木(agarwood) / 香炉(incense-burner) / 套装(gift-set)
