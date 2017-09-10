## Docker加速器
---

### 安装
#### 去除旧版本docker

  ```
  yum remove docker docker-engine docker.io
  ```

#### 安装Docker（建议>1.10）
  ```
  curl -sSL     http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -
  ```

#### 修改/etc/docker/daemon.json文件
  ```
  vi /etc/docker/daemon.json

  sudo mkdir -p /etc/docker
  sudo tee /etc/docker/daemon.json <<-'EOF'
  {
    "registry-mirrors": ["https://0wrm7oqo.mirror.aliyuncs.com"]
  }
  EOF
  sudo systemctl daemon-reload
  sudo systemctl restart docker
  ```


#### 设置开机自启

```
systemctl enable docker
```
### 问题

- 安装docker出错
  > log: Delta RPMs disabled because /usr/bin/applydeltarpm not installed

  解决办法：
  ```
  yum provides '*/applydeltarpm'
  yum install deltarpm
  ```

- 安装很慢
  不安装也可以的，从[阿里]("https://dev.aliyun.com/search.html")直接搜索也可以。


- 建议 使用yum源直接安装docker
