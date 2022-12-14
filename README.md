# 一、编译部署

转到项目根目录, 安装`hexo`依赖库（根据package.json文件）
```
npm install
```

本地部署调试, 地址 http://localhost:4000/
```
deploy-local-server.cmd
```

部署至`Github Pages`(第一次会有认证，根据输出信息进行权限认证), 在`_config.yml`中的`deploy`部分有设置, 地址 https://gis2all.github.io/
```
deploy-github-pages.cmd
```

建议先本地部署调试，如正常再部署更新至`Github Pages`, 这是因为`Github Pages`使用`Github Actions`有次数限制

说明
- `main` 分支 - 博客框架, 编译生成静态页面
- `deployment` 分支 - 静态页面, 部署至 `Github Pages`
- `Discussions` 功能 - 博客的评论系统

---

# 二、常用命令

<details>
<summary>点击查看常用命令</summary>

转到根目录吗, 使用如下命令:
```
hexo new [layout] <title>

# 例子, 在 _post目录下新增 test.md 文件, title为 "test"
# hexo new page --path _posts/test "This is test project"
```

其他常用命令
```
# 清理
hexo clean

# 生成
hexo generate

# 部署至本地
hexo server

# 部署至Github Pages
hexo deploy
```

</details>

# 三、博客主题

<details>
<summary>点击查看详细配置信息</summary>

主题使用的是 [butterfly](https://github.com/jerryc127/hexo-theme-butterfly), 安装方式使用`npm`所以在第一步时已经安装, 更改主题参考 [官方文档](https://butterfly.js.org/)

默认不修改主题里的任何文件, 在项目中使用 `npm install` 安装完依赖后, 主题的相对路径为 `node_modules\hexo-theme-butterfly`, 将主题中的资源等文件放至项目中的资源目录, 这样在主题更新时不会覆盖资源文件,

```
# 更新主题
npm update hexo-theme-butterfly
```

引用资源, 默认配置路径位于`node_modules\hexo-theme-butterfly\source`, 所以你会发现这样引用图片
```
# Avatar (头像)
avatar:
  img: /img/avatar.jpg
  effect: false
```

那么其实在项目的`source`目录对应主题的`source`目录, 且项目的`source`目录优先级更高, 所以直接在项目的`source`目录引用资源文件即可 (自己新建`asset`目录用来存放资源文件)

```
# Avatar (头像)
avatar:
  img: /asset/theme_avatar_2.jpg
  effect: false
```

主题中的 `_config.yml`和 项目中的 `_config.butterfly` 都是主题的配置文件, 但是后者优先级更高, 在 `_config.butterfly` 文件中配置主题事项

</details>

# 四、评论系统

<details>
<summary>点击查看详细配置信息</summary>

这里使用`giscus`集成评论系统

需要确保以下条件已完成：
- 仓库是 public类型.
- 仓库开启 Discussions. Repo -> Settings -> General -> Features -> Discussions
- [giscus app](https://github.com/apps/giscus) 在Github已安装


![image](/source/asset/readme_1.png)

转到 [giscus.app](https://giscus.app/zh-CN) 填写repo, 进而获取 repo, repo_id, category_id等值, 将其拷贝填写至主题配置文件 `_config.butterfly.yml`中的 giscus项

![image](/source/asset/readme_2.png)

重新编译部署后测试后测试, 就可以在博客中添加评论了, 在仓库的Discussions中可以更改删除评论, 同时会同步至博客

![image](/source/asset/readme_3.png)

</details>

# 五、文章搜索

<details>
<summary>点击查看详细配置信息</summary>

安装 `hexo-generator-search`, 默认第一步已安装所有依赖库
```
npm install hexo-generator-search --save
```

使用本地搜索功能, 编辑 `_config.butterfly.yml`
```
# Local search
local_search:
  enable: true
  preload: true
  CDN:
```

配置 `_config.yml`
```
# 搜索系统
# https://github.com/wzpan/hexo-generator-search
# 去掉 template 才能编译成功
search:
  path: search.xml
  field: all
  content: true
```

</details>

# 其他

<details>
<summary>项目如何初始化</summary>

安装`npm`, 使用`npm`安装`hexo`
```
npm install -g hexo-cli
```

新建`hexo`项目, 这里命令会自动创建所有文件结构
```
hexo init <folder>
```

Github新建一个空repo, `<username>.github.io`, clone至本地, 将`<folder>`目录下的除`.git`外的所有文件拷贝至空repo目录下,这样就完成项目的初始化 (之所以这么做是因为hexo不允许非空目录下新建项目, 绕了一个弯)

</details>