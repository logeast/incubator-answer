# 贡献指南

## 前端

https://answer.apache.org/zh-CN/blog/apache-answer-frontend-configuration-guide

```bash
cd ./ui
pnpm install
pnpm start
```

## 后端

```bash
go mod download
go run cmd/answer/main.go init -C ./answer-data
```

注：如果第一条跑不出来可先跑第二条，运行时间可能较长，请耐心等待。

看到 [SUCCESS] 即运行成功，注意此时不要关闭该程序。在网页输入所提示的网址：http://localhost:80/install/，打开并进行下一步安装。

注：如果打开网址找不到此localhost页面，尝试先运行以下命令再重试

```
cd ./ui
pnpm pre-install
pnpm install
pnpm build
```

运行

```bash 
go run cmd/answer/main.go run -C ./answer-data
```

