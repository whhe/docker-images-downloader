# Docker 镜像下载器

[English](README.md) | 简体中文

一个用于缓存 Docker 镜像文件的 GitHub Action。

## 使用

fork 并 clone 本仓库，并根据需要下载的镜像名称创建 git tag，GitHub Action 将会把镜像文件 `image.tar` 存储在 Artifacts 中。

注意：
- 因为 git tag 中不能有 `:`，因此你需要使用 `--` 来代替镜像名称中的 `:`。
- 默认情况下，GitHub Action 在 fork 仓库里是未启用的，因此你可能需要手动启用它。请参阅[文档](https://docs.github.com/en/actions/using-workflows/disabling-and-enabling-a-workflow?tool=webui#enabling-a-workflow)。

现在假设你要下载 Docker 镜像 `testcontainers/ryuk:0.5.1`，那么你应该在项目目录执行以下命令：

```shell
# 'testcontainers/ryuk--0.5.1' 代表镜像 'testcontainers/ryuk:0.5.1'
git tag testcontainers/ryuk--0.5.1
git push origin --tags
```

tag 推送后将自动触发 GitHub Action，你可以进入你的 fork 仓库的 [actions](https://github.com/whhe/docker-images-downloader/actions) 页面，在最新的 workflow 页面查看执行详情。

GitHub Action 的 workflow 完成后，您可以从 Artifacts 部分下载镜像文件，然后通过以下命令加载 Docker 镜像：

```shell
unzip image.zip
docker load -i image.tar
```

## 许可证

请参阅 [LICENSE](LICENSE)。