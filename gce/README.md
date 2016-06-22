## Google Cloud Engine特别说明(动态inventory)

1.首先需要创建一个[Service Account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount)并下载对应的son格式的[credentials](https://support.google.com/cloud/answer/6158849?hl=en&ref_topic=6262490#serviceaccounts)

2.下载[gce.py](https://raw.githubusercontent.com/ansible/ansible/devel/contrib/inventory/gce.py)和[gce.ini](https://raw.githubusercontent.com/ansible/ansible/devel/contrib/inventory/gce.ini)

3.配置认证数据

- 方法一[推荐]

  创建secrets.py，内容如下：

  ```python
  GCE_PARAMS = ('<步骤一创建的Service Account>', '<步骤一下载的json凭证完整路径>')
  GCE_KEYWORD_PARAMS = {'project': '<项目ID>'}
  ```

  记得将该文件从版本库中忽略


- 方法二

  将gce.ini中对应的gce_service_account_email_address、gce_service_account_pem_file_path和gce_project_id填写一下

4.使用ansible-playbook -i gce.py xxxx.yml -e "hosts=mars ansible_ssh_user=xxx"进行操作

### tips

查看机器列表：

```shell
python gce.py --list
```



## Google Cloud Engine网络模块操作

1、首先使用vault建立自己的gce_config.yml：

```shell
ansible-vault create gce_config.yml
```

输入密码后，在弹出的默认编辑器中配置自己的gce认证数据：

```yaml
---
service_account_email: xxxx@developer.gserviceaccount.com
credentials_file: /path/to/your/gce_credentials.json
project_id: your_project_id
```

2、修改gce_net.yml并使用以下命令运行：

```shell
ansible-playbook gce_net.yml -e @gce_config.yml --ask-vault-pass
```

## tips:

创建实例

```shell
ansible-playbook create_instance.yml -e @gce_config.yml -e "names=abc" --ask-vault-pass
```

删除实例

```shell
ansible-playbook destroy_instance.yml -e @gce_config.yml -e "names=abc" --ask-vault-pass
```



