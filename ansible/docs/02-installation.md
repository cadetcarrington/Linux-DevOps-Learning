# 02 · Ansible 安装与环境配置

## 安装

```zsh
python -m pip install ansible

ansible --version
ansible-playbook --version
```


## 构建清单

这里的清单可以将受管理的节点集中在文件中，为ansible提供系统信息和网络位置，我门可以通过构建清单文件用单个文件管理大量主机。

1. 创建  inventory.ini 文件。
2. 在文件中添加新的[host]组，并指定所有主机的IP地址（FQDN）。

```ini
[local]
localhost ansible_connection=local

[compute]
inspur2 ansible_host=10.108.17.56 ansible_user=cadetcarrington
inspur3 ansible_host=10.108.17.57 ansible_user=cadetcarrington
```

3. 验证
```zsh
ansible-inventory -i inventory.ini --list
```
4. ping
```zsh
ansible all -m ping -i inventory.ini
```
### INI与YAML

ini适用于简单少量的节点（好看）、YAML适用于大量的机器

```yml

compute:
    hosts:
        inspur2:
            ansible_host: 10.108.17.56
        inspur3:
            ansible_host:10.108.17.57
local:
    host:
        localhosts:
            ansible_connection:local
vars:
    ansible_user: cadetcarrington
    ansible_port:22

inspur:
    children:
        compute:
        local:
```
