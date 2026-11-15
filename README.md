# 目标链 mubiaolian.com

初高中知识目标站：把各学科的知识点组织成「目标链」——按学段与难度串联的主干知识环，每个考点可追溯前置必备、可跳转后续延伸，并关联对应的真题练习与公开讲解视频。

**在线访问**：<https://www.mubiaolian.com>

## 页面一览

| 文件 | 说明 |
|---|---|
| `mubiaolian-math.html` | 全学段数学（站点首页） |
| `mubiaolian-chinese.html` | 语文 |
| `mubiaolian-english.html` | 英语 |
| `mubiaolian-physics.html` | 物理 |
| `mubiaolian-chem.html` | 化学 |
| `mubiaolian-bio.html` | 生物 |
| `mubiaolian-pol.html` | 政治 |
| `mubiaolian-hist.html` | 历史 |
| `mubiaolian-geo.html` | 地理 |
| `gaokao.html` | 高考真题门户（真题 PDF 不在本仓库，见下方说明） |
| `about.html` | 关于本站 |
| `404.html` / `robots.txt` / `sitemap.xml` / `_headers` | 部署配套文件 |

## 特性

- 纯静态、单文件实现，无框架、无构建、无后端
- 知识点以「主干环 + 子考点」链式图谱呈现，节点点击查看详情
- 支持前置必备追溯与后续延伸跳转
- 内嵌公开讲解视频链接与真题年份定位
- 深浅配色克制，桌面与移动端均可使用

## 部署

任意静态托管均可。以 nginx 为例：

```nginx
server {
    listen 443 ssl;
    server_name www.mubiaolian.com;
    root /var/www/mubiaolian;
    index mubiaolian-math.html;
    error_page 404 /404.html;

    # HTML：允许短缓存，回源校验
    location ~* \.html$ {
        add_header Cache-Control "no-cache, must-revalidate";
    }
    # 真题 PDF：内容不变，长缓存
    location /gaokao/ {
        add_header Cache-Control "public, max-age=604800";
    }
}
```

`_headers` 为同样的缓存策略声明（Cloudflare Pages 格式），换用其他平台时可直接使用。

## 关于真题 PDF

`gaokao.html` 所链接的历年真题 PDF 来自公开网络渠道（各省考试院公开试卷等），**不随本仓库分发**。如需重建该目录，请自行从页面中的来源渠道获取。

## 免责声明

- 本站内容仅供个人学习交流使用，请勿商用
- 讲解视频与试题均链接或引用自公开网络渠道，本站仅做整理，不存储、不售卖任何资源
- 如认为内容侵犯您的权益，请联系 <contact@mubiaolian.com>，核实后 24 小时内下架

## 许可

代码以 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh) 授权：署名-非商业性使用-相同方式共享。
