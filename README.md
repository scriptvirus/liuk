# 静态部署说明

本项目是纯静态前端页面，可直接部署到 Nginx、Apache 或任意静态文件服务器。

## 目录说明

- `index.html`：主入口
- `page1.html` 到 `page8.html`：各功能页面
- `assets/vendor/`：本地化的第三方前端依赖

## 部署方式

将整个项目目录上传到服务器静态目录即可，例如：

```bash
/var/www/legal-tools/
```

Nginx 示例：

```nginx
server {
    listen 80;
    server_name your-domain.com;

    root /var/www/legal-tools;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

## 说明

- 当前改动只做了第三方依赖本地化，页面结构、样式和功能逻辑未调整。
- 如需完全离线使用，还需要保证 `assets/vendor/` 下的依赖文件完整可用。
