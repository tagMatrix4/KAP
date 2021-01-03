# KAP 

> @GoHack 2019

# PPT: [GoHack.pdf](./GoHack.pdf)

## desc
* 在构建阶段对可执行文件进行重新打包
* 在执行前经过安全检查和安全加载
* 主要可以防止以下安全问题：
  1. 服务器/二进制文件被重新打包窃密
  2. 二进制文件在非可靠生产环境运行
  3. 反调试
  4. 控制可执行用户权限
  5. 监控可执行文件被更改

## build

```
go mod download
bash build.sh
```

## run
```
需要代理, 但是还是提示缺少文件, 没有继续折腾
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
```

# go build xxx.go


* web
```
./bin/web/web
```

* packer
```
./bin/packer/packer <host>:5000 <Appid> <src file> <dst file>
```

* agent
```
./bin/agent -path <dst file> -host <host>:5000
```

## use flow

1. reg new appid

```
http POST :5000/app/new < test/app_new.json
```

2. pack

3. agent load encrypted file

4. (FOR InfoSec&OP) check security alert
