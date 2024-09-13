# 微信地区
 &emsp;&emsp;打开文件夹`/data/data/com.tecent.mm/`

搜索`mmregioncode`

找到`mmregioncode_zh_cn.txt`文件

把自己定位的省市那一行删除

打开微信  改地区 用定位

<hr>

# V2ray+Cloudflare+BBR
> BBR

    wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh

> V2ray

     yum install -y curl
     bash <(curl -sL https://raw.githubusercontent.com/hiifeng/v2ray/main/install_v2ray.sh)

配置：4

> Cloudflare

安全性→设置→安全级别→本质上为关

SSL/TLS:完全

端口:8443


# 宝塔命令
### 宝塔关闭安全入口 
```sh
rm -f /www/server/panel/data/admin_path.pl
```
### 卸载宝塔：
```sh
wget http://download.bt.cn/install/bt-uninstall.sh
sh bt-uninstall.sh
```


# X-UI+BBR
 > BBR
```sh
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```
> X-UI
```sh
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```



# Typecho 添加博主在线时间
将以下代码放在主题文件`functions.php`， 或core/core.php文件里

```php
    function get_last_login($user){
    $user   = '1';
    $now = time();
    $db     = Typecho_Db::get();
    $prefix = $db->getPrefix();
    $row = $db->fetchRow($db->select('activated')->from('table.users')->where('uid = ?', $user));
    echo Typecho_I18n::dateWord($row['activated'], $now);
    }
```
然后在想要显示的位置调用以下代码
```php
    博主 <?php get_last_login(1); ?> 在线
```
