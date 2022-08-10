安装 hexo 依赖库（根据package.json文件）
```
npm install
```

本地部署调试
```
hexo clean
hexo server
```

部署至Github Pages (第一次会有认证，根据输出信息进行权限认证)
```
hexo clean
hexo deploy
```

建议先本地部署调试，如正常再部署更新至Github Pages，这是因为 Github Pages使用 Github Actions有次数限制