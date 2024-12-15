# 贡献指南

## 前端

https://answer.apache.org/zh-CN/blog/apache-answer-frontend-configuration-guide

```bash
cd ./ui
pnpm install
pnpm start
```

## 后端

https://answer.apache.org/zh-CN/blog/apache-answer-backend-configuration-guide

```bash
go mod download
go run cmd/answer/main.go init -C ./answer-data
```

注：如果第一条跑不出来可先跑第二条，运行时间可能较长，请耐心等待。

看到 [SUCCESS] 即运行成功，注意此时不要关闭该程序。在网页输入所提示的网址：http://localhost:80/install/，打开并进行下一步安装。

注：如果打开网址找不到此 localhost 页面，尝试先运行以下命令再重试

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

## 插件

https://answer.apache.org/zh-CN/blog/how-to-package-and-deploy-answer-plugins

### 把插件仓库添加到项目中

使用 submodule 添加插件仓库

```bash
git submodule add https://github.com/apache/incubator-answer-plugins.git plugins
```

初始化和更新 submodule

```bash
git submodule init
git submodule update
```

更新插件代码

```
cd plugins
git pull origin main
cd ..
```

或者一条命令更新所有 submodule

```
git submodule update --remote
```

## 项目结构

这是一个名为 Apache Answer 的开源问答系统项目，让我为您分析其主要结构：

核心目录结构：

1. 后端部分：

- `cmd/`: 包含主程序入口和命令行相关代码
- `internal/`: 内部实现代码
- `pkg/`: 可复用的工具包
- `plugin/`: 插件系统相关代码
- `configs/`: 配置文件

2. 前端部分：

- `ui/`: React 前端项目
  - `src/`: 源代码
  - `public/`: 静态资源
  - `scripts/`: 构建脚本

3. 插件系统：

- `plugins/`: 官方插件
  - `cache-redis/`: Redis 缓存插件
  - `captcha-basic/`: 基础验证码插件

4. 部署相关：

- `charts/`: Helm charts 用于 Kubernetes 部署
- `docker-compose.yaml`: Docker Compose 配置
- `Dockerfile`: Docker 镜像构建文件

5. 项目配置文件：

- `.github/`: GitHub Actions 工作流配置
- `.gitlab-ci.yml`: GitLab CI 配置
- `.goreleaser.yaml`: Go 发布配置
- `go.mod`/`go.sum`: Go 依赖管理

6. 文档和许可：

- `README.md`: 项目说明
- `LICENSE`: Apache 2.0 许可证
- `NOTICE`: 版权声明
- `contributing.md`: 贡献指南

主要特点：

1. 采用插件化架构，支持多种功能扩展
2. 支持多语言国际化 (i18n)
3. 完善的 CI/CD 配置
4. 支持多种部署方式 (Docker, Kubernetes)
5. 前后端分离的架构设计

这是一个结构完整、工程化程度较高的开源项目，具有良好的可维护性和扩展性。
