#ansible-scripts

---
+ ssh.yml: 设置证书登录等

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
	

