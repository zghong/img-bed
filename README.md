# img-bed

## 基于 GitHub+PicGo 的免费图床解决方案

目前主要使用 markdown 作为笔记、博客等的写作工具，使用的客户端是[vscode](https://code.visualstudio.com/)和[有道云笔记](http://note.youdao.com/)，但是有道云笔记自带的图床是需要付费的，并且如果不使用图床的话，markdown 笔记的迁移也很麻烦。

目前主流的图床工具有，SM.MS 图床、腾讯云 COS、微博图床、GitHub 图床、七牛图床、Imgur 图床、阿里云 OSS、又拍云图床等。而这里边，SM.MS 和 Imgur 有免费版（诸多限制）也有收费版，腾讯云、七牛、阿里云、又拍云都是收费的，微博图床据说已经挂了，那么就剩下 GitHub 安全、免费又可靠了。

### GitHub 图床

- 创建新仓库，用于存储图片。
  - 仓库必须是`Public`的，否则外网无法访问仓库内的图片。
- `Settings`-`Developer settings`-`Personal access tokens`-`Generate new token`
  - 勾选`repo`权限，用于操作仓库。
  - 保存生成的 token。**这串 token 只会显示一次，注意保存。**

### PicGo 配置

- 仓库名：GitHub 用户名/repository 名
- 分支名：需要上传图片到哪个分支，推荐使用非 master 分支
- token：上一步保存的 token 值
- 存储路径（可选）：指定仓库下的某个文件夹
- 自定义域名（可选）：自定义域名的作用是，在上传图片后成功后，PicGo 会以`自定义域名+上传的图片名`的方式生成的访问链接，放到剪切板上。一般自定义域名用于 CDN 加速，例如`https://cdn.jsdelivr.net/gh/zghong/img-bed`

### 注意事项

#### jsDelivr 加速

由于国内环境的影响，GitHub 一直处于半墙不墙的状态，访问速度十分感人，所以使用 CDN 加速就很有必要了。

[jsDelivr](https://www.jsdelivr.com/)是一个免费、开源的加速 CDN 公共服务，托管了许多大大小小的项目，可加速访问 github、npm、wordpress 托管的项目目录或图片资源。下面说明一下加速 GitHub 的方法。

```shell
# 格式
https://cdn.jsdelivr.net/gh/用户名称/仓库名称@版本号/目录

# 示例
//加载资源（版本号不填的话，默认引用最新）
https://cdn.jsdelivr.net/gh/zghong/img-bed/img/01.png
//打开目录（后面的"/"是必要的，不然的话，打不开）
https://cdn.jsdelivr.net/gh/zghong/img-bed/
```

#### 无意义 commit

图床每增加一张图片，就会提交一次 commit，这样会导致好像显得你很活跃，但是真正点进去会发现你的代码更新并没有你真正提交 commit 的频率高。
