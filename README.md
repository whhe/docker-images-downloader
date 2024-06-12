# Docker Images Downloader

A GitHub Action to cache Docker image files.

## Usage

Fork the repository and create a tag by Docker image name, and then the Docker image file `image.tar` will be stored in the `image.zip` in GitHub Action Artifacts.

Note: you should use `--` to represent `:` in the tag name.

For example, you want to download the Docker image `testcontainers/ryuk:0.5.1`, then you should execute the following commands:

```shell
# 'testcontainers/ryuk--0.5.1' represents image 'testcontainers/ryuk:0.5.1'
git tag testcontainers/ryuk--0.5.1
git push origin --tags
```

After the GitHub Action executed, you can download the zip file from the 'Artifacts' section of the action webpage. You can load the Docker image by the following commands:

```shell
unzip image.zip
docker load -i image.tar
```

## License

See [LICENSE](LICENSE).