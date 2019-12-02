# trtis_cuda

由于编译依赖众多，所以采用镜像内编译：

1. 构建编译镜像

git clone git@code.byted.org:wangxiaohui.neo/trtis_cuda.git

git clone https://github.com/NVIDIA/tensorrt-inference-server.git

cp -r trtis_cuda tensorrt-inference-server/src/custom/byseqlib 

cd tensorrt-inference-server && git checkout r19.05

docker build -t tensorrtserver_build --target trtserver_build . (使用众多境外依赖库，可在dockerfile设置http_proxy)

nvidia-docker run -it --rm -v/${path}/${to}/tensorrt-inference-server/src:/workspace/src tensorrtserver_build （19.03版本docker以前）

或者 docker run --gpus all -it --rm -v/${path}/${to}/tensorrt-inference-server/src:/workspace/src tensorrtserver_build（19.03版本docker及以后）

2. 在镜像内

cd /workspace

bazel build -c opt src/servers/trtserver

bazel build -c opt src/custom/...
