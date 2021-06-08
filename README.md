## 修罗之战挂机程序

---

拒绝修罗, 从我做起; 打 NM 的修罗, 开 NM 的修罗; 建议关闭  
如果对逻辑有问题请自行修改源码: [查看源码](https://github.com/moxcomic/majsoul-api/tree/main/go)

## Quick Start

---

首先到[Release](https://github.com/moxcomic/no-asura-no/releases/latest)页面下载两个文件, 具体根据自己系统版本进行下载;  
本体: `majsoulex_asura`  
辅助: `rpc_helper`  
证书: `!!! 重要 !!! 身份认证文件必须有不能自己新建文件夹 !!!` `cer`文件夹

确认三个文件都下载完成后放到同一目录按照以下顺序执行:

1. 执行`majsoulex_asura`
2. `!!!重要!!! 不等只会摸切!!!` 等待出现`输入`
3. 执行`rpc_helper`
4. `输入`雀魂账号
5. `输入`雀魂密码
6. 等待`登录`与`二次连接`提示
7. 先用其他账号开一个`友人房`
8. 使用`joinroom 房间ID`进入房间先开一局友人

- 注意有`空格`

9. 确认进入游戏没有问题后`直接退出`, `也可以打完`
10. 输入`pipei`会自动进行修罗匹配

## for Android

1. 安装`termux`
2. 将 termux 的软件源换成清华源

```
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list
sed -i 's@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@' $PREFIX/etc/apt/sources.list.d/game.list
sed -i 's@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@' $PREFIX/etc/apt/sources.list.d/science.list
apt update && apt upgrade
```

3. 安装完整的`linux`系统(这里以 centos 举例)

```
pkg i proot
termux-chroot
echo "deb [trusted=yes arch=all] https://yadominjinta.github.io/files/ termux extras" >> $PREFIX/etc/apt/sources.list.d/atilo.list
apt update && apt install atilo-cn
atilo pull centos
atilo run centos
```

4. 安装 screen

```
yum install epel-release -y
yum install screen -y
cd /var/run/
chmod -R 777 screen/
```

5. 回到 root 目录下下载`雀魂Ex`挂机对应软件

```
cd /root
curl http://majserver.sykj.site:20008/asura/android/majsoulex_asura_linux_arm64_android -o ./majsoulex_asura_linux_arm64_android
curl http://majserver.sykj.site:20008/asura/android/rpc_helper_arm64_android -o ./rpc_helper_arm64_android
mkdir ./cer
curl http://majserver.sykj.site:20008/asura/android/cer/ca.crt -o ./cer/ca.crt
curl http://majserver.sykj.site:20008/asura/android/cer/client.key -o ./cer/client.key
curl http://majserver.sykj.site:20008/asura/android/cer/client.pem -o ./cer/client.pem
chmod +x ./majsoulex_asura_linux_arm64_android
chmod +x ./rpc_helper_arm64_android
```

6. 开启`两个screen`分别运行两个对应程序即可

```
screen -S maj
./majsoulex_asura_linux_arm64_android
# 等待出现输入账号密码页面
# CTRL + A + D 返回
screen -S rpc
./rpc_helper_arm64_android
# 此处必须提示 Demo已连接 ，否则请关闭两个软件重新启动
# CTRL + A + D 返回
screen -r maj
# 输入账号
# 输入密码
# 输入SendKey，可不填直接回车
# 等待登录完成
# 之后按照下方命令操作
```

## for iOS

1. 在`App Store`安装`iSH Shell`
2. 替换清华源

```
sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
```

3. 安装必要软件

```
apk add curl
apk add screen
```

4. 下载`雀魂Ex`挂机对应软件

```
curl http://majserver.sykj.site:20008/asura/ios/majsoulex_asura_linux_ios -o ./majsoulex_asura_linux_ios
curl http://majserver.sykj.site:20008/asura/ios/rpc_helper_linux_ios -o ./rpc_helper_linux_ios
mkdir ./cer
curl http://majserver.sykj.site:20008/asura/android/cer/ca.crt -o ./cer/ca.crt
curl http://majserver.sykj.site:20008/asura/android/cer/client.key -o ./cer/client.key
curl http://majserver.sykj.site:20008/asura/android/cer/client.pem -o ./cer/client.pem
chmod +x ./majsoulex_asura_linux_ios
chmod +x ./rpc_helper_linux_ios
```

5. 开启`两个screen`分别运行两个对应程序即可

```
screen -S maj
./majsoulex_asura_linux_arm64_android
# 等待出现输入账号密码页面
# CTRL + A + D 返回
screen -S rpc
./rpc_helper_arm64_android
# 此处必须提示 Demo已连接 ，否则请关闭两个软件重新启动
# CTRL + A + D 返回
screen -r maj
# 输入账号
# 输入密码
# 输入SendKey，可不填直接回车
# 等待登录完成
# 之后按照下方命令操作
```

## Commands

---

pipei: 进行修罗匹配, 结束后会自动进行再次匹配  
unpipei: 取消一局结束后进行自动匹配  
cancel: 取消匹配, 未匹配进入对局时有效  
vote: 同意投票结束  
joinroom: 进入友人房间, 例: joinroom 10086 (`注意空格`)  
leave: 离开友人房  
ready: 友人房准备  
discard: 出牌, 某些时候卡住时用 例: discard 1z true (true 表示摸切 false 表示手切)  
exit: 退出程序

## Author

---

B 站 ID: [神崎·H·亚里亚](https://space.bilibili.com/898411/)  
B 站 ID: [关野萝可](https://space.bilibili.com/612462792/)  
QQ 交流群: [991568358](https://jq.qq.com/?_wv=1027&k=3gaKRwqg)

请作者喝一杯咖啡

<figure class="third">
    <img src="https://moxcomic.github.io/wechat.png" width=170>
    <img src="https://moxcomic.github.io/alipay.png" width=170>
    <img src="https://moxcomic.github.io/qq.png" width=170>
</figure>
