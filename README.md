#ansible-scripts

---
+ ssh.yml:
 + 证书登录设置
 + 变更ssh端口(默认22)
 + 变更是否允许密码登录(默认禁止)


---
##运行说明

运行脚本的命令：

```
ansible-playbook <playbook> --extra-var="hosts=<目标主机>"
```

如：

```
ansible-playbook ssh.yml --extra-var="hosts=all"
```

Debian或Ubuntu需要root权限时请加上"-K"参数，如：

```
ansible-playbook ssh.yml --extra-var="hosts=all"
```
	

