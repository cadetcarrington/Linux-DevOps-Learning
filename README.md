# Linux & DevOps Learning

个人 Linux、DevOps 与 HPC 集群自动化学习仓库，记录理论笔记、命令示例和动手实验。

A personal learning repository for Linux system administration, DevOps, infrastructure automation, and HPC cluster management.

## 学习目录

| 方向 | 内容 | 状态 |
| --- | --- | --- |
| [Ansible](./ansible/README.md) | 自动化配置、Inventory、Playbook、Roles 与 Linux/HPC 实践 | 学习中 |
| Linux | 系统管理与日常运维 | 计划中 |
| Shell | Shell 脚本和批量任务 | 计划中 |
| Docker | 容器与部署 | 计划中 |
| Slurm | HPC 作业调度及集群管理 | 计划中 |

## 仓库组织原则

- 每个技术主题使用独立的顶层目录。
- `README.md` 用于导航，`docs/` 用于学习笔记，`playbooks/` 等目录保存可复现实验。
- 文档优先说明实验环境、执行步骤、预期结果、常见问题。
- 公开仓库只提交脱敏配置与示例，**禁止上传密码、SSH 私钥、访问令牌及真实内网资产信息**。

## 参考资料

- [Ansible 官方文档](https://docs.ansible.com/ansible/latest/)
- [Ansible GitHub 源码仓库](https://github.com/ansible/ansible)

> 此仓库以学习记录为主，示例自动化脚本应在测试环境验证后再用于生产或共享集群。
