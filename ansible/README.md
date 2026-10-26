# Ansible Learning

使用 Ansible 学习 Linux 自动化运维与 HPC 集群管理。这里集中维护学习路线、笔记索引和可复现的实验代码。

> 项目目录：`Linux-DevOps-Learning/ansible/`。请在此目录运行以下命令，以使用对应的 `ansible.cfg`。

## 快速开始

第一次使用请先学习 **[02 · 安装与环境配置](./docs/02-installation.md)**。

安装完成后，从仓库的 `ansible/` 目录运行：

```bash
ansible --version
ansible-inventory --list
ansible local -m ansible.builtin.ping
ansible-playbook playbooks/hello.yml
```

以上命令默认仅在**本机**执行，不会连接远程服务器。

## 学习路线

### 第一阶段 · 基础入门

- [x] [01 · Ansible 简介](./docs/01-introduction.md)
- [x] [02 · 安装与环境配置](./docs/02-installation.md)
- [ ] 03 · Inventory 主机清单

### 第二阶段 · 基础操作

- [ ] 04 · Ad-Hoc 临时命令
- [ ] 05 · YAML 与 Playbook
- [ ] 06 · 常用自动化模块

### 第三阶段 · 进阶编排

- [ ] 07 · 变量与逻辑控制
- [ ] 08 · Jinja2、Handlers 与执行控制
- [ ] 09 · Roles 与 Collections

### 第四阶段 · 工程与实战

- [ ] 10 · 调试与最佳实践
- [ ] 11 · Linux 自动化运维
- [ ] 12 · HPC 集群自动化（Slurm、Rocky Linux 等）

> 上面的勾选表示**对应章节文档已经建立**，不代表已完成学习。后续创建对应章节时再添加链接。

## 仓库文件说明

| 路径 | 说明 |
| --- | --- |
| [docs/](./docs/) | 按学习路线组织的 Markdown 笔记 |
| [inventories/hosts.example.ini](./inventories/hosts.example.ini) | 仅包含 localhost 的安全示例主机清单 |
| [playbooks/hello.yml](./playbooks/hello.yml) | 第一个只读的本机 Playbook |
| [ansible.cfg](./ansible.cfg) | 本学习项目的基础配置 |

如需管理远程测试主机，可将 `hosts.example.ini` 复制为 `hosts.ini` 后修改实际目标地址，并通过 `-i inventories/hosts.ini` 显式指定主机清单。**不要提交真实凭据、SSH 私钥或敏感服务器信息**。

## 参考资料

- [Ansible 官方文档](https://docs.ansible.com/ansible/latest/)
- [Ansible Getting Started](https://docs.ansible.com/ansible/latest/getting_started/index.html)
- [Ansible GitHub 源码](https://github.com/ansible/ansible)
