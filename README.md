# k8s依赖的docker镜像
## 概述
 每次安装k8s集群时，镜像都是一个问题，为了避免每次都要去各种找镜像，干脆不如自己打包生成镜像。

## 操作步骤
1. 修改Dockerfile的版本
2. 打标签
3. 登录docker hub并生成镜像
4. 为了考虑获取更好的速度，可以将镜像上传到阿里云

## 参考
[国内获取k8s镜像](https://blog.csdn.net/sjyu_ustc/article/details/79990858)
