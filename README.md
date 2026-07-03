# 合成大头像

一个纯前端手机网页小游戏，玩法类似“合成大西瓜”。玩家控制顶部头像掉落位置，相同等级头像碰撞后会合成更高等级头像，最高等级为第 5 级。

## 本地打开方法

直接双击 `index.html` 即可运行。不需要 `npm install`，不需要后端，不需要数据库，也不需要启动服务器。

## 照片放置位置

5 张照片必须放在：

- `assets/face-1.png`
- `assets/face-2.png`
- `assets/face-3.png`
- `assets/face-4.png`
- `assets/face-5.png`

## 如何替换照片

用新的 PNG 图片替换 `assets/` 目录里的同名文件即可。建议使用正方形照片；如果不是正方形，游戏会按圆形头像方式居中裁剪，类似 `object-fit: cover`，不会拉伸变形。

## 如何上传 GitHub

1. 在 GitHub 新建一个仓库。
2. 把本项目里的 `index.html`、`style.css`、`game.js`、`README.md` 和 `assets/` 文件夹一起上传。
3. 确认 `index.html` 在仓库根目录，不要放进 `assets/`。

## 如何开启 GitHub Pages

1. 打开 GitHub 仓库页面。
2. 进入 `Settings`。
3. 找到 `Pages`。
4. Source 选择 `Deploy from a branch`。
5. Branch 选择 `main`，目录选择 `/root`。
6. 保存后等待几分钟，GitHub 会生成一个网页地址。

## 别人玩是否需要 GitHub 账号

不需要。只要你的 GitHub Pages 仓库是公开可访问的，别人打开链接就能玩。

## 是否需要买域名

不需要。GitHub Pages 会提供免费的默认域名。如果以后想用自己的品牌域名，再单独绑定自定义域名即可。

## 如何修改游戏标题

修改 `index.html` 里的 `<title>` 和页面中的 `<h1>` 文本即可。如果还想同步修改 README，也可以改本文档标题。

## 如何修改头像等级数量

主要修改 `game.js`：

1. 在 `imagePaths` 数组里增加或减少图片路径。
2. 在 `levelConfig` 数组里增加或减少对应等级的半径、颜色和光圈配置。
3. 最高等级由 `levelConfig.length - 1` 自动决定。

同时记得在 `assets/` 里放入对应图片。

## 如何修改分数规则

在 `game.js` 搜索：

```js
score += (level + 1) * 10;
```

把这行改成你想要的分数公式即可。

## 常见问题排查

### 图片不显示怎么办

检查图片是否放在 `assets/` 目录下，文件名是否严格为 `face-1.png` 到 `face-5.png`。大小写和后缀都要一致。图片加载失败时，游戏会自动显示彩色圆球和等级数字，不会崩溃。

### 手机页面会滚动怎么办

本项目已经在 `html`、`body`、游戏容器和 `canvas` 上设置了 `touch-action: none`、`overflow: hidden` 和触摸事件 `preventDefault`。如果仍然滚动，优先检查是否改动了 `style.css` 或把游戏嵌入到了其他可滚动页面中。

### GitHub Pages 打开 404 怎么办

确认 `index.html` 在仓库根目录，Pages 的 Branch 选择了正确分支，目录选择 `/root`。刚开启 Pages 后可能需要等待几分钟。

### Matter.js 加载失败怎么办

本项目通过 CDN 加载 Matter.js：

```html
https://cdn.jsdelivr.net/npm/matter-js@0.19.0/build/matter.min.js
```

如果网络无法访问该 CDN，可以换成其他可信 CDN，或下载官方 Matter.js 文件后在本地引用。不要从不明网站下载脚本。

### 微信打不开怎么办

先确认链接是 HTTPS，GitHub Pages 默认是 HTTPS。微信里如果加载慢，可以复制链接到手机浏览器打开。若页面空白，通常是 Matter.js CDN 被网络拦截，换网络或换可信 CDN 后再试。
