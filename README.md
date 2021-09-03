# vue-element-admin-template

本项目的 [开发文档](spider-admin-pro.md)

基于 [vue-admin-template](https://github.com/PanJiaChen/vue-admin-template) 改造的一个后台管理模板

整合和扩展的内容包括：
Vue
Element UI
Axios
iconfont
permission control

## 二次开发

```bash
# 克隆项目
git clone git@github.com:mouday/spider-admin-pro-web.git

# 进入项目目录
cd spider-admin-pro-web

# 安装依赖
npm install

# 或者使用cnpm
cnpm i

# 建议不要直接使用 cnpm 安装以来，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npm.taobao.org

# 启动服务
npm run dev
```

浏览器访问 [http://localhost:9528](http://localhost:9528)

## 发布

```bash
# 发布前端代码，用于和后端代码整合打包
npm run dep-pub
```
