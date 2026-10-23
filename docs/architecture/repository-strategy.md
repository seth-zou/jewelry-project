# 五仓库策略

| 仓库 | 职责 | 部署物 | 上游依赖 | 默认分支 |
| --- | --- | --- | --- | --- |
| `jewelry-platform` | 后端业务 API、验真 API、异步 worker、调度任务 | Spring Boot jar / container image | `jewelry-ledger` 合约接口、`jewelry-infra` 部署模板 | `main` |
| `jewelry-web` | 管理后台、合作方门户、消费者 H5 | Static site bundle | `jewelry-platform` API | `main` |
| `jewelry-ledger` | Go Chaincode 领域逻辑、Fabric 网络治理模板 | Chaincode package / governance docs | 架构 ADR | `main` |
| `jewelry-infra` | Terraform、Helm、GitOps、Runbook | Terraform plan、Helm release、GitOps manifests | 各代码仓镜像与配置 | `main` |
| `jewelry-project` | 跨仓架构、ADR、规划、治理和中间产物索引 | 文档 | 全部仓库 | `main` |

## 版本策略

- 五仓默认分支均为 `main`。
- 运行时代码使用 SemVer 风格 tag，例如 `platform-v0.1.0`、`web-v0.1.0`。
- `jewelry-infra` 通过 GitOps 环境目录引用镜像 tag，避免隐式 latest。
- ADR 采用不可变编号，变更通过新 ADR 取代旧决策。
