# Leancloud-Bing
运行在Leancloud的Bing每日壁纸前端页面

#### 在线地址
https://bing.avosapps.us/


### 简介

- 轻量、迅速、无占用
- 优雅的响应式前端界面，可静态部署

- 前后端分离，后端接口可单独部署
- 又拍云存储加速
- 丰富的接口功能

众所周知，必应搜索官网每天会更新一张高质量的背景图。许多同学想在接口中调用它们，但必应的服务器在国内不算特别稳定（>500ms）。项目可以把每天的必应图片上传至又拍云，提供支持图片处理、回溯的接口（又拍云直链，实测从请求到图片接收完成耗时300ms左右，视网络情况而不同），并可选部署优雅的前端页面。


### 部署

#### 1、部署后端服务
> 前端项目运行需要后端服务
> [详见后端项目](https://github.com/LiteraturePro/Leancloud-Bing-Api)

#### 2、部署前端服务

> 前端可以纯静态部署，部署在各大静态托管或者OSS服务商。

> 为了提升您的访问速度，建议为前端页面部署CDN加速。

CDN建议的缓存设置如下：

缓存7天：

```
/*.(htm,html,js,css,png,svg,ico,ttf,otf,woff,woff2,eot,sfnt)
```

不缓存：

```
/*.(php,json)
```

- 目录结构

      .
      ├── css
      │   ├── detail.css
      │   ├── index.css
      │   └── main.css
      ├── html
      │   └── detail.html
      ├── index.html
      ├── js
      │   ├── detail.js
      │   ├── index.js
      │   └── main.js
      ├── lib
      │   ├── bootstrap.min.css
      │   ├── bootstrap.min.css.map
      │   ├── bootstrap.min.js
      │   ├── bootstrap.min.js.map
      │   ├── jquery-1.11.0.js
      │   ├── progressive-image.css
      │   ├── progressive-image.js
      │   └── Valine.min.js
      └── sass
          ├── detail.scss
          ├── index.scss
          └── main.scss
        
2.1、配置评论系统
请在 `detail.js` 中修改评论系统 Valine 的信息：

参考 [Valine 官方文档](https://valine.js.org/)

建议就直接配置托管后端的应用，托管前端的也行，前提是前端托管在Leancloud上.

```
appId: '********'
appKey: '********'
```
2.2、配置域名

为了最快的响应速度，前端页面为纯静态，请查找并替换以下文件中的域名：

```
index.html
html/detail.html
js/detail.js
js/index.js
js/main.js
```

替换方法：

1. 全局搜索替换，将 `https://bing.avosapps.us/` 替换为您部署后端得到的域名。
2. 将 `js/main.js` 中的 `https://bing-upcdn.wxiou.cn/` 替换为您的又拍云存储加速域名。

2.3 部署服务

将项目fork到自己的仓库，不想fork,新建都行；
参考Leancloud的[云引擎Git部署文档](https://leancloud.cn/docs/leanengine_quickstart.html),几个配置，简简单单。


#### 鸣谢原作者
- [androidmumo](https://github.com/androidmumo/Bing-upyun)
