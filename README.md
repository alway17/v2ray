# v2ray
最好用的 V2Ray 一键安装脚本 &amp; 管理脚本

## 教程

要求：Ubuntu 14+ / Debian 7+ / CentOS 7+ 系统的小鸡鸡
推荐使用 Debian 9 系统，脚本会自动启用 BBR 优化。
备注：不推荐使用 Debian 8 系统，因为 Caddy 申请证书可能会出现一些莫名其妙的问题

## 安装 V2Ray
输入下面命令回车，你可以复制过去，然后在 Xshell 界面按 Shift + Insert 即可粘贴，不能按 Ctrl + V 的。。
使用 root 用户输入下面命令安装或卸载

bash <(curl -s -L https://233yes.com/v2ray.sh)

如果233yes该网站被和谐,则该代码是否会生效？试试结尾的GitHub安装

如果提示 curl: command not found ，那是因为你的 VPS 没装 Curl
ubuntu/debian 系统安装 Curl 方法: apt-get update -y && apt-get install curl -y
centos 系统安装 Curl 方法: yum update -y && yum install curl -y
安装好 curl 之后就能安装脚本了

注意事项：如果你是 CentOS 7 系统，此脚本会关闭 firewalld 并且使用 iptables
## 备注：安装完成后，输入 v2ray 即可管理 V2Ray
如果提示你的系统不支持此脚本，那么请尝试更换系统


## 管理面板
v2ray info 查看 V2Ray 配置信息 
v2ray config 修改 V2Ray 配置 
v2ray link 生成 V2Ray 配置文件链接 
v2ray infolink 生成 V2Ray 配置信息链接 
v2ray qr 生成 V2Ray 配置二维码链接 
v2ray ss 修改 Shadowsocks 配置 
v2ray ssinfo 查看 Shadowsocks 配置信息 
v2ray ssqr 生成 Shadowsocks 配置二维码链接 
v2ray status 查看 V2Ray 运行状态 
v2ray start 启动 V2Ray 
v2ray stop 停止 V2Ray 
v2ray restart 重启 V2Ray 
v2ray log 查看 V2Ray 运行日志 
v2ray update 更新 V2Ray
v2ray update.sh 更新 V2Ray 管理脚本
v2ray uninstall 卸载 V2Ray

## 配置文件路径

V2Ray 配置文件路径：/etc/v2ray/config.json
Caddy 配置文件路径：/etc/caddy/Caddyfile
脚本配置文件路径: /etc/v2ray/233blog_v2ray_backup.conf

警告，请不要修改脚本配置文件，免得出错。。
如果你不是有特别的需求，也不要修改 V2Ray 配置文件
不过也没事，若你实在想要瞎折腾，出错了的话，你就卸载，然后重装，再出错 ，再卸载，再重装，重复到自己不再想折腾为止。。

## 备注

V2Ray 客户端配置文件 SOCKS 监听端口为 2333， HTTP 监听端口为 6666
可能某些 V2Ray 客户端的选项或描述略有不同，但事实上，此脚本显示的 V2Ray 配置信息已经足够详细，由于客户端的不同，请对号入座。

目前只支持配置一个 V2Ray 账号…不支持 Shadowsocks 多用户。。不支持 SSR。。
使用国际大厂的 VPS，请自行在安全组 (防火墙) 开放端口和 UDP 协议 (如果你要使用含有 mKCP 的传输协议)

## 一些技巧
担心 IP 被墙？
看这里：使用 Cloudflare 中转 V2Ray WebSocket 的流量来避免 IP 被墙

# 优化 V2Ray
由于本人的脚本在 Debian9 系统会自动开启 BBR 优化加速了，所以不需要再安装 BBR 优化了，
如果你还是觉得网络比较慢的话，你可以尝试使用含有 mKCP 的传输协议，这个 mKCP 的东东，简单一点说就像 Kcptun 一样加速，并且还能进行伪装 (可选)，但是由于 mKCP 是使用 UDP 协议的，也许运营商会限速得更加厉害，网络变得更加慢。但不管怎么样，你都可以随时尝试一下。
服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再接着选择 mKCP 相关的传输协议即可
如果你是使用其他商家的 VPS 并且是按照此教程流程来安装 V2Ray 的话，那么你可以输入 v2ray bbr 回车，然后选择安装 BBR 或者 锐速 来优化 V2Ray
只是还想再啰嗦一下，如果你是使用国际大厂的 VPS，并且是按照此教程流程来安装 V2Ray 的话，请自行在安全组 (防火墙) 开放端口和 UDP 协议 (如果你要使用含有 mKCP 的传输协议)

## WebSocket + TLS
实现 WebSocket + TLS 超级无敌简单，前提是要拥有一个能正常解析的域名 (并且知道怎么解析域名)
服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再选择 WebSocket + TLS，即是输入 4，接着输入你的域名，然后我都懒得说了，脚本都那么简单明了，我还瞎BB干嘛…
哈哈…可能有不少人在折腾 V2Ray 实现 WS + TLS 的时候真的是搞到很蛋痛咯，有些人的教程可能说得不是很清楚，或者是直接忽略小白萌新这些亲爱的用户，嗯，小白们好好加油吧，请尽量多学一些基础知识，别总是做伸手党，对于毫无交集的陌生人，人家并没有任何义务要帮你的啊
偷偷跟你说…使用 WebSocket + TLS 会有断流的问题
多说一句，不要被某些人带节奏，WS + TLS 并不是 V2Ray 的神级配置，该墙还是会墙，墙你不需要理由
备注一下啦，这里我没写怎么教你注册域名啦，怎么解析域名啦，如果你真的想要使用 WebSocket + TLS，那就 自己谷歌摸索一下，其实好简单的啦！
我本人并没有在使用 WS + TLS (WebSocket + TLS)，我用 TCP，就是用一键脚本全程回车的那种懒人

## HTTP/2
实现 HTTP/2 (h2) 也超级无敌简单，和 WebSocket + TLS 一样，也就是只要一个域名就够
服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再选择 HTTP/2，即是输入 16，然后………看上面的 WebSocket + TLS 的相关。
备注一下，HTTP/2 相比 WS + TLS (WebSocket + TLS) ，在浏览网页时有一些优势。速度是差不多的啦

## mKCP
mKCP 这个东东其实就是 KCP 协议，反正你知道是能提速的就行，但是不保证都能提速，还能避免 TCP 阻断，但是也可以会被运营商 Qos.
使用方法：服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，之后再选择 mKCP 相关的就行

## 备份
为了避免由于不可抗拒的原因所造成本人主动删除脚本，所以建议请将本脚本 Fork 一份
备份地址： https://github.com/233boy/v2ray/fork
安装方法，确保你已经 Fork 了脚本，将 233boy 修改成你的 Github 用户名

git clone https://github.com/233boy/v2ray
cd v2ray
chmod +x install.sh
./install.sh local

如果提示 git 命令不可用，那就自己安装咯，不会安装啊？我也不知道啊。哈哈


哪个传输协议好？
心中无杂念，用 TCP
ISP 常作怪，用 动态端口
小鸡速度不好，用 mKCP
处子之身，用 WS + TLS


TCP 阻断
如果你觉得你的小鸡出现了这种情况，那么可以尝试使用 UDP 协议相关的 mKCP
当然，用了我的脚本那是很简单的啦，直接输入 v2ray config 然后选择修改 V2Ray 传输协议
之后再选择 mKCP 相关的就行咯
备注：使用 mKCP 或许还可以提高速度，但由于 UDP 的原因也许会被运营商 Qos，这是无解的。
