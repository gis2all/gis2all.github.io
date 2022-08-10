安装 hexo 依赖库（根据package.json文件）
```
npm install
```

本地部署调试, 地址http://localhost:4000/
```
deploy-local-server.cmd
```

部署至Github Pages (第一次会有认证，根据输出信息进行权限认证), 在`_config.yml`中的deploy部分有设置
```
deploy-github-pages.cmd
```

建议先本地部署调试，如正常再部署更新至Github Pages，这是因为 Github Pages使用 Github Actions有次数限制

主题使用的是 [butterfly](!https://github.com/jerryc127/hexo-theme-butterfly), 安装方式使用 npm 所以在第一步时已经安装, 更改主题参考官方文档