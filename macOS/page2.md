# mac OS 下修改被默认占用的80端口

由于mac OS是自带Apache服务的，它本身占用了 **80** 端口，首先你需要将Apache的监听端口改为其他或者直接将其卸载，这里我们把他改成 **8011**

- 命令行

```bash
sudo vim /etc/apache2/httpd.conf
```

```xml
#Listen 12.34.56.78:80
<IfDefine SERVER_APP_HAS_DEFAULT_PORTS>
    Listen 8080
</IfDefine>
<IfDefine !SERVER_APP_HAS_DEFAULT_PORTS>
    Listen 80
</IfDefine>
```

将 Listen 中的 **80**  改为 **8011** 然后使用命令将其重启

```bash
sudo /usr/sbin/apachectl restart
```

