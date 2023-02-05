port: 7890
socks-port: 7891
allow-lan: false
bind-address: '*'
mode: rule
log-level: info
ipv6: false
external-controller: 127.0.0.1:9090
interface-name: en0
dns:
  enable: true
  listen: 0.0.0.0:53
  default-nameserver:
    - 119.29.29.29
    - 119.28.28.28
    - 223.5.5.5
    - 114.114.114.114
  nameserver:
    - https://dns.alidns.com/dns-query
    - https://doh.dns.sb/dns-query
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  fake-ip-filter:
    - '*.lan'
    - localhost.ptlogin2.qq.com
    - '+.srv.nintendo.net'
    - '+.stun.playstation.net'
    - '+.msftconnecttest.com'
    - '+.msftncsi.com'
    - '+.xboxlive.com'
    - 'msftconnecttest.com'
    - 'xbox.*.microsoft.com'
    - '*.battlenet.com.cn'
    - '*.battlenet.com'
    - '*.blzstatic.cn'
    - '*.battle.net'
  
proxies:
  - name: sj
    type: vless
    server: sj.252798.xyz
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "sj.252798.xyz"
  - name: jp
    type: vless
    server: jp.252798.xyz
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "jp.252798.xyz"
  - name: sj1
    type: vless
    server: sj.alichen.top
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "sj.alichen.top"
  - name: jp1
    type: vless
    server: jp.alichen.top
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "jp.alichen.top"
  - name: hka
    type: vless
    server: hka.252798.xyz
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "hka.252798.xyz"
  - name: kr
    type: vless
    server: kr.252798.xyz
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "kr.252798.xyz"
  - name: la
    type: vless
    server: la.252798.xyz
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "la.252798.xyz"
  - name: la2
    type: vless
    server: la2.alichen.top
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "la2.alichen.top"
  - name: la3
    type: vless
    server: la3.alichen.top
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "la3.alichen.top"
  - name: la5
    type: vless
    server: la.alichen.top
    port: 443
    skip-cert-verify: true
    uuid: 6373c273-4a52-4e5d-9ee9-afd23107bdc3
    tls: true
    network: grpc
    grpc-opts:
      grpc-service-name: "la.alichen.top"
      grpc-multi-mode: true

  
proxy-groups:
   # 代理节点选择
  - name: "PROXY"
    type: select
    proxies:
      - hka
      - kr
      - sj
      - sj1
      - jp
      - jp1
      - la
      - la2
      - la3
      - la5

rule-providers:
  reject:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/reject.txt"
    path: ./ruleset/reject.yaml
    interval: 86400

  icloud:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/icloud.txt"
    path: ./ruleset/icloud.yaml
    interval: 86400

  apple:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/apple.txt"
    path: ./ruleset/apple.yaml
    interval: 86400

  google:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/google.txt"
    path: ./ruleset/google.yaml
    interval: 86400

  proxy:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/proxy.txt"
    path: ./ruleset/proxy.yaml
    interval: 86400

  direct:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/direct.txt"
    path: ./ruleset/direct.yaml
    interval: 86400

  private:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/private.txt"
    path: ./ruleset/private.yaml
    interval: 86400

  gfw:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/gfw.txt"
    path: ./ruleset/gfw.yaml
    interval: 86400

  greatfire:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/greatfire.txt"
    path: ./ruleset/greatfire.yaml
    interval: 86400

  tld-not-cn:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/tld-not-cn.txt"
    path: ./ruleset/tld-not-cn.yaml
    interval: 86400

  telegramcidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/telegramcidr.txt"
    path: ./ruleset/telegramcidr.yaml
    interval: 86400

  cncidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/cncidr.txt"
    path: ./ruleset/cncidr.yaml
    interval: 86400

  lancidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/lancidr.txt"
    path: ./ruleset/lancidr.yaml
    interval: 86400

  applications:
    type: http
    behavior: classical
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/applications.txt"
    path: ./ruleset/applications.yaml
    interval: 86400

rules:
  - RULE-SET,applications,DIRECT
  - DOMAIN,clash.razord.top,DIRECT
  - DOMAIN,yacd.haishan.me,DIRECT
  - RULE-SET,private,DIRECT
  - RULE-SET,reject,REJECT
  - RULE-SET,icloud,DIRECT
  - RULE-SET,apple,DIRECT
  - RULE-SET,google,DIRECT
  - RULE-SET,proxy,PROXY
  - RULE-SET,direct,DIRECT
  - RULE-SET,lancidr,DIRECT
  - RULE-SET,cncidr,DIRECT
  - RULE-SET,telegramcidr,PROXY
  - GEOIP,LAN,DIRECT
  - GEOIP,CN,DIRECT
  - MATCH,PROXY
