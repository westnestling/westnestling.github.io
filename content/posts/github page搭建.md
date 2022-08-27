搭建静态页面网站有几种技术选型：Hogo是Go语言，Hexo是nodejs，jekyll是Ruby

jekyll 的优势是方便，Github 本身有内核支持深度绑定，项目中直接添加配置文件开始写文本就行。windows不推荐安装ruby环境，并且不支持部分私密不可见。

hexo 的优势是速度快，中文社区，缺点是每次更新内容都需要执行严格的语法检查，然后再次部署。

Hugo 简介响应快，简单，社区活跃

> Gitee `Pages` 是一个免费的静态网页托管服务，您可以使用 Gitee `Pages` 托管博客、项目官网等静态网页。如果您使用过 `Github Pages` 那么您会很快上手使用 Gitee 的 `Pages`服务。目前 Gitee `Pages` 支持 Jekyll、Hugo、Hexo编译静态资源。
>
> Jekyll、Hugo、Hexo 编译判断依据
>
> 1. 编译 Hugo 依据：仓库编译目录下存在`config.toml|json|yaml`文件和`content`目录的时候，会使用`hugo`生成静态文件。
> 2. 编译 Hexo 依据：仓库编译目录下存在`package.json`，`_config.yml`文件和`scaffolds`目录的，会使用`hexo generate`生成静态文件，由于每次部署编译需要重新克隆编译并进行`npm install`，所以使用 Hexo 的时间相对 Hugo 和 Jekyll 会长一些。
> 3. 当不符合上述1和2条件的时候，就默认使用Jekyll编译。



### jekyll

主题：https://github.com/topics/jekyll-theme



### Hugo

社区：https://discourse.gohugo.io/

主题：https://themes.gohugo.io/themes/hugo-theme-learn/

安装：https://gohugo.io/getting-started/installing/



#### 安装

