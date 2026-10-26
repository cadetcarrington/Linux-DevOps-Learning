# 01 · Ansible 简介

## 1. Ansible 是什么

Ansible 是一款 IT 自动化工具，常用于 Linux 服务器的批量管理、配置管理、应用部署和任务编排。

核心思想：在**控制节点（Control Node）**安装并运行 Ansible，根据**主机清单（Inventory）**确定目标服务器，通过 SSH 等连接方式执行任务。多数常见 Linux 场景不要求在被控节点部署常驻 Ansible Agent。

## 2. 核心术语

| 概念 | 作用 |
| --- | --- |
| Control Node | 执行 Ansible 命令的机器 |
| Managed Node | 被 Ansible 管理的目标机器 |
| Inventory | 描述目标主机与主机分组 |
| Ad-Hoc | 一次性的命令或任务 |
| Module | 执行具体动作的模块，如 `ping`、`copy`、`package` |
| Playbook | 由 YAML 编写的自动化任务流程 |
| Role | 将任务、变量、模板等整理为可复用组件 |
| Collection | 分发模块、插件、角色等内容的打包机制 |

## 3. Ansible 的常见特点

- **Agentless**：典型 Linux SSH 管理场景通常无需部署常驻 Agent。
- **声明式配置和幂等性**：不少配置管理模块能够在目标已经满足期望状态时不再重复修改；但不是所有命令和任务天然幂等。
- **可读性**：使用 YAML 表达自动化流程。
- **批量管理**：根据 Inventory 对多台机器或主机组执行任务。

## 4. 常用命令

```bash
ansible --version
ansible-inventory --list
ansible localhost -m ansible.builtin.ping
ansible-playbook playbooks/hello.yml
```

以上示例假定工作目录为仓库中的 `ansible/`，并已完成[第 02 章安装](./02-installation.md)。

## 5. 面向 HPC 的目标

学习完成后，尝试使用 Ansible 自动化：

1. 批量维护 Linux 用户及 SSH 公钥。
2. 统一安装节点所需软件包。
3. 维护多节点 Slurm 的部分配置与服务。
4. 在测试节点验证后，逐步应用于集群。

> 生产集群的账户、服务和网络配置变更具有风险，先使用测试环境与 `--check`、`--diff` 验证。

## 参考资料

- [Ansible 官方文档](https://docs.ansible.com/ansible/latest/)
- [Ansible Getting Started](https://docs.ansible.com/ansible/latest/getting_started/index.html)
- [Ansible GitHub](https://github.com/ansible/ansible)
