# Docker Images Downloader

English | [简体中文](README_CN.md)

A GitHub Action to cache Docker image files.

## Usage

Fork and clone this repository and create a tag by Docker image name, and then the Docker image file `image.tar` will be stored in the `image.zip` in GitHub Action Artifacts.

Note: 
- There must not be `:` in git tag, so you should use `--` to represent `:` in the tag name.
- Workflows are not being run on forked repository by default, so you should enable it manually. See [docs](https://docs.github.com/en/actions/using-workflows/disabling-and-enabling-a-workflow?tool=webui#enabling-a-workflow).

For example, you want to download the Docker image `testcontainers/ryuk:0.5.1`, then you should execute the following commands:

```shell
# 'testcontainers/ryuk--0.5.1' represents image 'testcontainers/ryuk:0.5.1'
git tag testcontainers/ryuk--0.5.1
git push origin --tags
```

A GitHub Action will be automatically triggered after the tag is pushed up. You can go to the [actions](https://github.com/whhe/docker-images-downloader/actions) page of your repository and check the execution details at the latest workflow page. 

After the GitHub Action workflow is complete, you can download the image file from the 'Artifacts' section, then you can load the Docker image by the following commands:

```shell
unzip image.zip
docker load -i image.tar
```

## License

See [LICENSE](LICENSE).