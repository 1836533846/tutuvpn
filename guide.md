https://www.vpscn.net/40.html
# �����ļ�
config.json
{
    "server": "xyk.azero-ng.cn",
    "server_ipv6": "::",
    "server_port": 443,
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "tutututu",
    "method": "aes-256-cfb",
    "protocol": "origin",
    "protocol_param": "",
    "obfs": "plain",
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}

#------------------------------ [ ShadowSocksR ] ------------------------------#
# ��װ
�޸�install_ssr.bash�е��ļ���װ��ַ��INSTALL_PATH= ����ǰ·����
# ����
# ����
bash install_ssr.bash start
# ����
curl -x socks5://localhost:1080 ip.cn

������ʲ��ˣ�ʹ��
bash install_ssr.bash config�鿴�����Ƿ���ȷ

#-------------------------------- [ Privoxy ] --------------------------------#
# ��װprivoxy
sudo pacman -S privoxy
# ���ã�/etc/privoxy/config ����

listen-address  127.0.0.1:1087  # Ĭ�� 8118
actionsfile gfwlist.action

# ��gfwlist.action�ŵ�privoxyȥ

sudo cp gfwlist.action /etc/privoxy/

# ����
sudo systemctl start privoxy.service
bash  install_srr.bash  start
# ���ԣ�
curl -x http://localhost:1087 ip.cn
curl -x http://localhost:1087 www.google.com

#���ֶ���������Ϊ����
http 127.0.0.1 1087
socks 127.0.0.1 1080

# ��������
sudo systemctl enable privoxy.service
sudo systemctl start ssr.service
sudo systemctl enable ssr.service

https://github.com/the0demiurge/CharlesScripts/blob/master/charles/bin/ssr
ͼ�ν���
https://github.com/erguotou520/electron-ssr/releases

ƻ���ֻ�SSR�ͻ��ˣ�Potatso Lite��Potatso��shadowrocket��������Ϊ
superwingy��firstwingy��shadowingy��wingy +�� banananet��kite-ss proxy��goodshadow��icproyx��shadowrocket�ȡ�

 ShadowsocksR�˺� ������Ϣ��

 I  P	    : xyk.azero-ng.cn
 �˿�	    : 443
 ����	    : tutututu
 ����	    : aes-256-cfb
 Э��	    : origin
 ����	    : plain

 Shadowsocks�˺� ������Ϣ��
 I  P	    : xyk.azero-ng.cn
 �˿�	    : 443
 ����	    : tutututu
 ����	    : aes-256-cfb

 SS    ���� :ss://YWVzLTI1Ni1jZmI6dHV0dXR1dHVAeHlrLmF6ZXJvLW5nLmNuOjQ0Mw==
 SSR   ���� :ssr://eHlrLmF6ZXJvLW5nLmNuOjQ0MzpvcmlnaW46YWVzLTI1Ni1jZmI6cGxhaW46ZEhWMGRYUjFkSFUvP29iZnNwYXJhbT0
