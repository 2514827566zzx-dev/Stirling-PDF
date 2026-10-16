# Stirling-PDF 可落地 Demo

本包用官方 Docker 镜像运行 Stirling-PDF，并附项目仓库自带的三页测试 PDF。可以直接体验拆分、页面整理和压缩，不需要上传自己的文件。ZIP 不包含上游仓库源码或 Docker 镜像。上游：[Stirling-Tools/Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF)；你的 Fork：[2514827566zzx-dev/Stirling-PDF](https://github.com/2514827566zzx-dev/Stirling-PDF)。

## 启动和体验

需要 Docker Engine/Desktop、Docker Compose v2+、Python 3 和可下载镜像的网络。建议至少 4 GB 可用内存。

1. 解压后运行 `python3 start.py`，脚本校验配置并启动 Stirling-PDF `3.2.0`。
2. 执行 `python3 verify.py`；预期 `/api/v1/info/status` 返回 `HTTP 200` 和 `UP`。
3. 打开 `http://127.0.0.1:3104`，在“拆分 PDF”或“整理页面”中上传 `examples/Stirling-Sample.pdf`，选取其中一页并下载结果；确认文件能打开。

样例文件保持上游原样，来自 [Stirling-PDF v3.2.0 仓库](https://github.com/Stirling-Tools/Stirling-PDF/blob/v3.2.0/frontend/editor/public/samples/Sample.pdf)，上游许可见 `examples/UPSTREAM-LICENSE.txt`。配置和处理数据使用 Docker 命名卷；`docker compose down` 不会删除它们。

## 部署边界

演示默认关闭登录，同时只绑定 `127.0.0.1:3104`。远程服务器上可通过 `ssh -L 3104:127.0.0.1:3104 用户@服务器` 安全访问。要做公网服务，先配置 HTTPS 和登录控制，再调整监听地址；不要直接开放无登录的 3104 端口。

参考：[官方 Docker 安装说明](https://docs.stirlingpdf.com/Server/Install/Docker/)。
