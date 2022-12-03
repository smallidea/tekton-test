<!--
 * @Date: 2022-12-02 17:47:54
 * @LastEditors: Jason Chen
 * @LastEditTime: 2022-12-03 15:29:59
 * @FilePath: /tekton-test/readme.md
-->

Tekton 的演示脚本

# 部署
以 linux / mac 为例
``` yaml

# docker & docker-compose install
curl -o- https://smartidedl.blob.core.chinacloudapi.cn/docker/linux/docker-install.sh | bash

# Kubectl install
curl -LO https://smartidedl.blob.core.chinacloudapi.cn/kubectl/v1.23.0/bin/linux/amd64/kubectl
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# minikube install，参考 https://minikube.sigs.k8s.io/docs/start/
curl -LO https://smartidedl.blob.core.chinacloudapi.cn/minikube/v1.24.0/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikub
minikube delete
minikube start --image-mirror-country=cn --driver=docker --cpus=2 --memory=2048mb

# Tekton Pipeline & Dashboard install
kubectl apply -f https://gitee.com/chileeb/SmartIDE/raw/main/server/deployment/online/pipeline/v0.32.0/smartide-tekton-release.yaml
kubectl apply -f https://gitee.com/chileeb/SmartIDE/raw/main/server/deployment/online/dashboard/v0.32.0/smartide-tekton-dashboard-release.yaml

# Tekton Trigger install （选装）
kubectl apply -f https://gitee.com/chileeb/SmartIDE/raw/main/server/deployment/online/trigger/v0.18.0/smartide-release.yaml
kubectl apply -f https://gitee.com/chileeb/SmartIDE/raw/main/server/deployment/online/trigger/v0.18.0/smartide-interceptor.yaml

# Tekton CLI
brew install tektoncd-cli

```

# 创建CRD资源
