# 02 · Ansible 安装与环境配置

本文记录在 Linux / macOS 控制节点上通过 Python 虚拟环境安装 Ansible 的过程。

## 1. 安装前检查

确保已安装 Python 3 和 `pip`，并满足当前 Ansible 版本的 Python 支持要求。

```bash
python3 --version
python3 -m pip --version
```

> 各版本支持的 Python 范围可能不同，以[官方安装指南](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)为准。

## 2. 创建 Python 虚拟环境

在本地终端执行：

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

建议把虚拟环境放在本地工作目录，仓库的 `.gitignore` 已排除 `.venv/`。

## 3. 安装 Ansible

原先记录的安装命令仍然适用：

```bash
pip install ansible
```

使用虚拟环境时，建议明确使用当前 Python 的 pip：

```bash
python -m pip install ansible
```

如果仅需轻量级核心引擎，也可以了解 `ansible-core`。完整 `ansible` 包还包含一批 Collections。

## 4. 验证安装

```bash
ansible --version
ansible-playbook --version
```

验证本地连接：

```bash
ansible localhost -i localhost, -c local -m ansible.builtin.ping
```

期望看到类似 `"ping": "pong"` 的结果，表示 Ansible 可以在本机执行模块；这**不表示 SSH 远程连接已经配置成功**。

## 5. 使用仓库中的示例

进入仓库的 `ansible/` 目录：

```bash
cd ansible
ansible-inventory -i inventories/hosts.example.ini --list
ansible-playbook -i inventories/hosts.example.ini playbooks/hello.yml
```

`hosts.example.ini` 默认只包含本机；远程服务器示例处于注释状态，不会尝试连接。

## 6. 远程连接的准备（后续学习）

1. 确保控制节点能通过 SSH 登录测试服务器。
2. 将 `inventories/hosts.example.ini` 复制成私有的 `inventories/hosts.ini`。
3. 只在本地填写真实主机地址、用户名，不要把私密凭据提交到公共仓库。
4. 使用 `ansible -i inventories/hosts.ini compute -m ansible.builtin.ping` 验证连接。

> 不要为了方便而全局关闭 SSH host key checking。生产或共享集群需要遵守现有运维授权和变更规范。

## 7. 常见问题

- `ansible: command not found`：检查虚拟环境是否已激活、Ansible 是否安装成功。
- `Permission denied (publickey)`：先独立验证 `ssh user@host`，检查公钥授权和用户名。
- `UNREACHABLE`：检查地址、DNS、网络连通性与 SSH 端口。
- `No module named ...`：确认当前 Python 环境与需要的依赖。

## 参考资料

- [Ansible Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Ansible Getting Started](https://docs.ansible.com/ansible/latest/getting_started/index.html)
