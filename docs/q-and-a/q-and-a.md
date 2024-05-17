# Q&A

## Subscription links do not update properly after configuring Cloudflare CDN

Set the following request expression as `Bypass cache` in the Caching - Cache Rules:

```
(http.request.uri.path contains "/sub")
```

## Will NeXT Panel add the xx protocol?

NeXT Panel currently supports Shadowsocks(2022), Vmess, Trojan, and TUIC, with Vmesss and Trojan protocols supporting the V2Ray transport plugin, and the Shadowsocks 2022 protocol supporting single-port multi-user.

## NeXT Panel supports VLESS/XTLS/REALITY...??

We believe that a well-designed proxy protocol does not need to have its underlying design repeatedly modified over its lifetime to effectively avoid censorship, and the original Trojan protocol is a good positive example of this. Even with the threat of advanced traffic censorship techniques such as active probing, deep packet inspection, and machine-learning based traffic analysis, it is still possible to penetrate most restricted network environments, and authoritarian regimes in places such as China and Iran would need to resort to extreme methods such as indiscriminate jamming of the TLS handshake, whitelisting of SNI domain names, artificial IP blacklists, and even localized internet blackouts to truly affect the operation of the original Trojan protocol. Trojan protocol.

Unfortunately, we didn't see this kind of development in the Xray project, instead we saw "revolutionary" technologies like VLESS, XTLS, etc. declared unsupported a few years after their introduction, and replaced with new "revolutionary" REALITY protocol. For an open source project like NeXT Panel, which relies on volunteers to contribute their time and effort, supporting a protocol that lacks long term stability and requires repeated changes to the back-end code to adapt after every major update is a costly endeavor.
