# Surge ʹ���ֲ�

Surge ����� iOS10 �ϵ�������������Ȼ��[����](http://nssurge.com/)˵�� Surge �ǿ����ߵ�������Թ��ߣ�������������Դ��ϼ�����������㷺��Ӧ�ó������԰��� **iOS10����** ��һ���裬iOS10������ Surge ֮��iPhone Խ��������������һ����

### ��Ҫ����

Surge ����Ҫ���ܰ������£�

- �ػ� iOS �ϵ�����Ӧ�ó���� HTTP/HTTPS/TCP �����������ض��� HTTP/HTTPS/SOCK5 ���������ת����
- ���� iOS ���������µ� DNS ���������ã�ʹ�� iOS �豸�����ڷ�������֮��ʱ��������Ҳ�ܹ����� DNS ��������
- ��¼�豸������/���յ� HTTP ����/Ӧ���ײ���Ϣ��
- ���û��� domain, domain suffix, domain keyword, CIDR IP �Լ� GeoIP �Ĺ��˹���
- ���豸�� WIFI�����������Լ��������ӻỰ����������ͳ���Լ����١�
- �� URL �� iTunes ����/���������ļ���
- �ض�ʹ�ó������кܸߵ������Լ���Ӧ�ԡ�
- ���� domain �������ι�档
- ��ȫ���ݷ������硣

�� iOS9֮ǰ��ҪԽ������ʹ�õ� Shadowsocks �Ƚϣ�Surge �� iPhone ��ǿ��Ŀ������ԣ����˹��򣩡�����ͳ���Լ���־����Ϊ�ź��������� iOS ɳ�̵����ƣ�Surge �޷�ʵ�� ``Ӧ���ڴ���`` ���ܣ�ϣ�������ж�Ӧ��Խ����������ֲ�������㡣

### �������

Ϊ����ʹ�����ܹ����õ���� Surge �ĸ������õ����ã������ڹ��������⻨��һ���½��������������

![Surge Architecture](https://manual.nssurge.com/Surge-Architecture.png)

Surge ��Ҫ���� **Surge proxy server** �� **Surge TUN interface** ������������ֱ��� HTTP/HTTPS �����Լ� IP ����

- Surge Proxy server: Surge ���ܿ������Զ����� iOS �豸�����е� HTTP/HTTPS ��ͬʱ�����е� HTTP/HTTPS ����ʹ��ͬһ������Ự��������޶���� Surge �Ĵ������ܡ�Surge ����ͨ�� ``skip-proxy`` ָ����Щ�������� proxy server ������

- Surge TUN interface: iOS �ϴ󲿷�Ӧ�ó�������罻��ʹ�� HTTP/HTTPS����Ҳ���ڲ���Ӧ�ó���(��:iOS�ʼ��ͻ��ˡ�Facebook�ͻ��ˣ���Ӧ�ó���ʹ��������ͨѶ��ʽ���磺SPDY�ȣ�����ЩӦ���޷��� Proxy server �����������Ҫʹ�ø�Ϊ�ײ��TUN interface �����ʽ��Surge ����ͨ�� ``bypass-tun`` ָ����Щ������������ TUN interface ����

> ע��: ��ǰ Surge TUN interface ֻ�ܴ��� TCP ���������� ICMP��UDP ��������ֱ�Ӷ����������Ҫͨ������ ``bypass-tun`` ѡ����������Щ������

### �����ļ�

Surge ����ͨ�� ``URL����`` �� ``iTunes����`` �����ַ�ʽ���������ļ��������ļ��ɶ����(Section)���ɣ���Ҫ����:General, Proxy, Rule�ȼ������֡�

#### ͨ������

ͨ�����ö�**[general]**����Ҫ��������:

```
[General]
loglevel = verbose
bypass-system = true
skip-proxy = 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12, localhost, *.local
bypass-tun = 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12
dns-server = 8.8.8.8, 8.8.4.4
```

##### loglevel 

Surge�������־��Ϣ���𣬰���־����Ӷൽ�ٷֱ�Ϊ verbose,info,notify��warning��Ĭ��Ϊ notify��һ������²�Ҫ����Ϊ verbose ��������Ƚ��� Surge �����ܣ����ֻ����Ϊ����ʹ�ã���������Ϊ������ٵ� warning ����

##### bypass-system

ȫ�ֺ������ã��������б���ָ���ķ������������������ᱻ Surge ���������� Proxy server �� TUN interface������һ��ʹ���У��뽫���·��������� bypass-system ��������ܻ����һЩ������⣨���磺Ӧ�ó�������ͱ��ӳ٣������ Apple ���õķ����������嵥��

```
api.smoot.apple.com
configuration.apple.com
xp.apple.com
smp-device-content.apple.com
guzzoni.apple.com
captive.apple.com
*.ess.apple.com
*.push.apple.com
*.push-apple.com.akadns.net
```

ͬʱҲ�� Apple �ķ����� IP ��ַ�ι��˹������ `IP-CIDR, 17.0.0.0/8, DIRECT, no-resolve` ��

##### skip-proxy

skip-proxy ����ָ����Щ��������**������IP**���� Proxy server �������õ����������÷�ʽ:

- ������������ apple.com
- �����ض��ؼ��ֵ��������� *apple.com
- �ض����������� store.apple.com
- �ض���IP��ַ�Լ�IP��ַ�Σ��� 192.168.2.11,192.168.2.*,192.168.2.0/24

������ʹ��ʱ�����Կ�����������ӳ��õ�Ӧ�õ������Լ������й������ IP ��ַ�Ρ�

> ��Ҫ�ر�˵����������Ӧ�ó����ر������󼶵�Ӧ�ã�һ�㶼�㷺���� CDN �����Է�����������м��٣����������ͬ�������ڲ�ͬ�ĵ�����ͬ������ͬʱ�䶼���ܻ����󵽲�ͬ IP ��ַ�����Ҫͨ����������ķ�ʽƥ�䣬�����ܲ��ü򵥵����ָ�� IP ��ַ��

##### bypass-tun

bypass-tun ����ָ����Щ������������/IP���� TUN interface ת�������õķ�ʽͬ skip-proxy����Ҫ�ر�ע����� Proxy server ��������������ᱻ TUNN interface ������������� bypass-tun ʱ��Ҫ��� skip-proxy �����ۺϿ��ǡ�

##### dns-server

dns-server ����ָ�� iOS �豸��ʹ�õ�����������������iOS �����ǲ������޸ķ��������µ�����������������ͨ��ʹ�� Surge �� dns-server ��������Դﵽ�޸ķ�����������������������Ŀ�ġ�

#### ��������

�������ö� **[Proxy]** �������� HTTP, HTTPS �Լ� SOCKS5 ��������������ӵĹؼ��������õ���������:

```
[Proxy]
ProxyA = socks5, example.server.com, 3129
ProxyB = http, example.server.com, 3128
ProxyC = https, example.server.com, 443, username, password
```

��������У��������������������ֱ��Ӧ�� HTTP, HTTPS �Լ� SOCKS5 �����ִ�����ƣ�Surge �����������������ָ�����ײ�ͬ�����ã�

- ָ�� HTTP/HTTPS ������û��������루��ѡ��
- ָ�� HTTPS ����ļ��ܻ��ƣ��� ``ProxyC = https, example.server.com, 443, username, password, cipher=TLS_RSA_WITH_AES_128_GCM_SHA256``
- ָ�� TLS �Ự�ش���HTTPS ����Ĭ�ϴ� ``False Start``��``ECN``���ܡ���δ���汾��֧�� on/off ���ã�

#### ���˹���

``[Rule]``���������� Surge �Ĺ��˹��򣬹�����洢��ƥ��ʱ���ϵ��£���ƥ������Ч����˶��ڳ��õĹ���Ӧ�÷���ǰͷ����������ܣ����õ���������:

```
[Rule]
DOMAIN-SUFFIX,company.com,ProxyA
DOMAIN-KEYWORD,google,DIRECT
GEOIP,US,DIRECT
IP-CIDR,192.168.0.0/16,DIRECT
FINAL ProxyB
```

Surge ֧�� DOMAIN,DOMAIN-SUFFIX,DOMAIN-KEYWORD,GEOIP,IP-CIDR��FINAL �����ֹ���ÿ�������� ���ͣ�ƥ�����Լ���Ϊ ���������ֹ��ɣ����� FINAL �����⣩��ÿ������ʹ�ö��Ÿ�����ÿ�������ָ������Ϊ����������(Proxy)��������DIRECT���Ͷ�����REJECT�������֡�

���ֹ��˹�����������£�

- DOMAIN����ȷָ��������`` DOMAIN,www.apple.com,Proxy ``��ƥ�����з��� www.apple.com ������
- DOMAIN-SUFFIX����������׺ƥ�䣬``DOMAIN-SUFFIX,apple.com,Proxy``��ƥ�����з����� apple.com ��β���������� store.apple.com,mail.apple.com�ȣ��������� issue-apple.com
- DOMAIN-KEWORD���������ؼ���ƥ�䣬``DOMAIN-KEYWORD,google,Proxy``��ƥ�����������а��� google ����������: www.google.com, issue-google.cn ��
- IP-CIDR���� IP ��ַ����ƥ�䣬`` IP-CIDR, 192.168.0.0/16,DIRECT``��ƥ�����е����� 192.168.0.0/16 ������
- GEOIP��������λ��IPƥ�䣬``GEOIP,US,DIRECT`` ƥ����������IP������
- FINAL������ƥ�����Ϊ���������������ָ��������ǰ������һ������ƥ���������Ϊ

> ע��REJECT ���˹����Ϲ������ƥ����Թ��˵�Ӧ�ó����ڲ���棬�����ĺܰ���

##### no-resolve

���� Rule ���� GEOIP �� IP-CIDR ����ʱ��Surge �������л���������������������������������ͨ����ѡ����``no-resolve`` ����ָ���ض������������������������磺

```
GEOIP,US,DIRECT,no-resolve
IP-CIDR,172.16.0.0/12,DIRECT,no-resolve
```

##### force-remote-dns

���� TCP Э���Ӧ�ó����� TUN interface ģʽ����Ҫ�������ʱ�����Ȼᷢ��������������֮���ٷ��� TCP ���ݣ���������޷��ڱ��ر�����������ͨ�� ``force-remote-dns`` ����������Զ�̴����Ͻ��н������磺

```
DOMAIN,www.apple.com,Proxy,force-remote-dns
DOMAIN-SUFFIX,apple.com,Proxy,force-remote-dns
DOMAIN-KEYWORD,google,Proxy,force-remote-dns
```

> ע��: ������� TUN interface ��Ч������ Proxy Server ���ԣ����е������ DNS ������Զ�̴����Ͻ����ġ�

#### ��������

������``#!REQUIRE-PROTECTED``��ͷ�����ö��Ǳ������ã����������� Surge ����н����ᱻ��ʾ�����㽫˽�����÷��͸������˹���ʱ���Խ�˽����Ϣ��Ϊ�������á�

> ע������Ҳûɶ�ã������ļ������ǿɶ��ģ������ļ�ֱ�ӿ������ˡ�

### URL Scheme

Surge ֧�� URL Scheme �����ض�/Ч��ʹ���ߵ����󣬲������ҹ��ƣ���������߲��뱻�磬���Ǿ������������ URL Scheme����Ȼ��ô�᲻֧���л������ļ��� URL Scheme����ǰ Surge ��֧��������Ϊ�Լ�һ��ѡ�

- ��Ϊ:start,stop,toggle
- surge:///start��ʹ��Ԥ��ѡ���ķ��������ÿ��� Surge ����
- surge:///stop���ر� Surge ����
- surge:///toggle����/�ر� Surge ����
- ѡ��:autoclose=true������Ϊִ�����ʱ���Զ��˳� Surge ��� ``surge:///toggle?autoclose=true`` 



