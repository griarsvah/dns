# DNS
DNS (Domain Name System) — система, которая переводит доменные имена в IP-адреса, которые необходимы для того, чтобы устройства в интернете могли обмениваться данными.

## Как работает DNS
Запрос: Когда вы вводите адрес сайта в браузере, например, www.example.com, ваш компьютер сначала обращается к серверу DNS, чтобы узнать, какой IP-адрес соответствует этому домену.

Решение: DNS-сервер отвечает с нужным IP-адресом. Этот процесс может включать несколько серверов, начиная от локального кэширования до использования более глобальных серверов (например, корневых серверов).

Соединение: Когда IP-адрес найден, ваш компьютер может установить соединение с веб-сервером, который хранит содержимое сайта.

## DNS records
1. A (Address)
Преобразует доменное имя в IPv4-адрес.
Пример: example.com. A 93.184.216.34

2. AAAA (IPv6 Address)
Преобразует доменное имя в IPv6-адрес.
Пример: example.com. AAAA 2606:2800:220:1:248:1893:25c8:1946

3. CNAME (Canonical Name)
Указывает, что домен является псевдонимом другого домена.
Пример: www.example.com. CNAME example.com.

4. MX (Mail Exchange)
Указывает почтовые серверы для домена.
Пример: example.com. MX 10 mail.example.com.

5. TXT (Text)
Хранит текстовую информацию, используется для верификации доменов, SPF/DKIM для электронной почты и другие нужды.
Пример: example.com. TXT "v=spf1 include:_spf.example.com ~all"

6. NS (Name Server)
Указывает на серверы имен для домена.
Пример: example.com. NS ns1.example.com.

7. PTR (Pointer)
Используется для обратного разрешения (Reverse DNS), т.е. преобразует IP-адрес в доменное имя.
Пример: 34.216.93.93.in-addr.arpa. PTR example.com.

8. SOA (Start of Authority)
Хранит информацию о зоне, такую как основной сервер имен, почтовый адрес администратора и параметры кэширования.
Пример: example.com. SOA ns1.example.com. admin.example.com. 2023032901 3600 1800 1209600 86400

9. SRV (Service)
Указывает расположение серверов для специфических сервисов (например, SIP, XMPP).
Пример: _sip._tcp.example.com. SRV 10 60 5060 sipserver.example.com.

10. CAA (Certification Authority Authorization)
Указывает, какие сертификаты SSL/TLS могут быть выданы для домена.
Пример: example.com. CAA 0 issue "letsencrypt.org"

11. NAPTR (Name Authority Pointer)
Используется для указания на преобразования доменных имён для специфических сервисов, например ENUM (для телефонных номеров).
Пример: example.com. NAPTR 100 10 "U" "E2U+sip" "!^.*$!sip:info@example.com!" .

12. HINFO (Host Information)
Хранит информацию о сервере, например, о его операционной системе и архитектуре.
Пример: example.com. HINFO "Linux" "x86_64"

13. MINFO (Mailbox Information)
Содержит информацию о почтовом ящике для уведомлений об ошибках.
Пример: example.com. MINFO mailbox.example.com.

14. MX (Mail Exchange)
Подробности записи для почтового обмена, указания приоритета и сервера.
Пример: example.com. MX 10 mail.example.com.

15. RP (Responsible Person)
Указывает почтовый ящик, который отвечает за домен.
Пример: example.com. RP person@example.com.

16. AFSDB (Andrew File System Database)
Связывает домен с AFS (Andrew File System) сервером.
Пример: example.com. AFSDB 1 host.example.com.

17. X25 (X.25)
Ранее использовался для указания маршрута X.25-сетей.
Пример: example.com. X25 host.example.com.

18. ISDN (Integrated Services Digital Network)
Содержит информацию о сервере для сетей ISDN.
Пример: example.com. ISDN tel:12345678

19. SIG (Signature)
Сигнатура для записи DNSSEC (Domain Name System Security Extensions).
Пример: example.com. SIG 3 1 1

20. KEY (Public Key)
Содержит открытый ключ для записи DNSSEC.
Пример: example.com. KEY 257 3 1

21. DS (Delegation Signer)
Запись, которая используется в системе DNSSEC для указания делегированных подписанных записей.
Пример: example.com. DS 12345 8 2 ...

22. DNAME (Delegation Name)
Похоже на CNAME, но может перенаправлять весь домен.
Пример: example.com. DNAME example.net.

23. TLSA (Transport Layer Security Authentication)
Используется для указания на сертификаты и аутентификацию TLS в DNS.
Пример: _443._tcp.example.com. TLSA 3 0 1 ...

24. URI (Uniform Resource Identifier)
Содержит URI для домена.
Пример: example.com. URI "https://example.com"

25. LOC (Location)
Хранит информацию о географическом местоположении серверов.
Пример: example.com. LOC 37 23 12N 122 5 13W 10m

26. DNSKEY (DNS Key)
Ключ для DNSSEC (обеспечивает безопасность).
Пример: example.com. DNSKEY 256 3 5 ...

27. NSEC (Next Secure)
Используется для DNSSEC, чтобы указать на отсутствие записи.
Пример: example.com. NSEC example.net.

28. NSEC3 (Next Secure 3)
Усиленная версия NSEC для DNSSEC, улучшенная для защиты от атак.
Пример: example.com. NSEC3 ...

29. NSEC3PARAM
Параметры для использования NSEC3 в DNSSEC.
Пример: example.com. NSEC3PARAM ...



===========

Чтобы с сайта на почту приходили письма, необходимо правильно настроить MX записи (Mail Exchange) для домена.
MX записи определяют, какие серверы будут обрабатывать входящие сообщения для данного домена.



Получить адреса почтовых серверов.
Это зависит от почтового провайдера, который обслуживает ваш домен (например, Google Workspace, Yandex, Mail.ru, или собственные серверы).
Каждый почтовый сервис имеет свои значения для MX записей.

Настройка MX записей:
В панели управления DNS вашего хостинга или регистратора доменов нужно добавить следующие MX записи.



Для Google Workspace:

Запись 1:
Тип записи: MX
Приоритет: 1
Значение: ASPMX.L.GOOGLE.COM

Запись 2:
Тип записи: MX
Приоритет: 5
Значение: ALT1.ASPMX.L.GOOGLE.COM

Запись 3:
Тип записи: MX
Приоритет: 5
Значение: ALT2.ASPMX.L.GOOGLE.COM

Запись 4:
Тип записи: MX
Приоритет: 10
Значение: ALT3.ASPMX.L.GOOGLE.COM

Запись 5:
Тип записи: MX
Приоритет: 10
Значение: ALT4.ASPMX.L.GOOGLE.COM



Для Yandex:

Имя:
домен
@ (для основного домена)
Оставить пустым
TTL: стандартное значение (3600 секунд)
Тип записи: MX (почтовый сервер)
Домен: mx.yandex.net.
Приоритет: 10








### Проверка работы MX записей:

После настройки MX записей потребуется некоторое время (обычно до 48 часов), чтобы изменения распространились по DNS.

####  Онлайн-сервисы для проверки правильности записей
https://mxtoolbox.com/
- MX Lookup: Этот инструмент позволяет проверить записи MX (Mail Exchange) для домена, чтобы убедиться, что почтовый сервер настроен правильно. Введите домен, например, example.com, и получите информацию о том, куда направляется почта для этого домена. 
- DNS Lookup: Проверяет DNS-записи для домена, включая A-запись, CNAME, MX и другие. Это полезно для диагностики проблем с разрешением доменов. 
- Blacklist Check: Проверяет, не попал ли ваш IP-адрес или домен в черные списки спам-серверов. Это поможет понять, почему ваше письмо может не доставляться. 
- SMTP Test: Анализирует SMTP-сервер и проверяет его работу, наличие ошибок или неправильных настроек. Это особенно полезно, если у вас возникают проблемы с отправкой почты. 
- Ping Test: Простой способ проверить доступность сервера по его IP-адресу или домену. Отправляет запросы на сервер и проверяет его отклик. 
- Traceroute: Отслеживает маршрут, по которому данные идут от вашего компьютера к серверу, показывая, на каком узле возникает задержка или проблема. 

```
[https://toolbox.googleapps.com/apps/checkmx/check](https://toolbox.googleapps.com/apps/main/)
https://dnschecker.org/mx-lookup.php
https://network-tools.webwiz.net/email-test.htm
https://www.gmass.co/smtp-test
```


#### Доп:
```
winget install swaks
```

```
swaks --to user@example.com --server smtp2.example.com
```

```
>winget install swaks
No package found matching input criteria.
```

```
>@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))"
```

```
choco --version
```

```
choco install swaks
```

```
choco install swaks --pre
```

https://github.com/jetmore/swaks/
---

https://jetmore.org/john/code/swaks/installation.html

Windows
There's no packaged version in Windows. The easiest way to install in Windows is to use the CPAN-packaged App::swaks. Keep in mind that a working Perl will need to be installed (Strawberry Perl and ActiveState Perl both work)

---

### Telnet
```
dism /online /enable-feature /featurename:TelnetClient
```

```
telnet
```
quit

```
> telnet smtp.yandex.ru 25
```

Telnet не поддерживает зашифрованные соединения (SSL/TLS). Это будет полезно только для проверки доступности порта, но не для фактического зашифрованного соединения.

```
swaks --help
```

```
sysdm.cpl
```

"Настройки почты" или "Настройки SMTP и POP/IMAP"
SMTP-сервер: smtp.yandex.ru
Порты:
465 для SSL
587 для TLS



#### Важные моменты:
MX записи для домена совпадают с рекомендациями почтового провайдера
MX-записи определяют, на какой сервер отправляется почта для твоего домена. Если почта не отправляется, возможно, проблема в этих записях.
SMTP-сервер отвечает за отправку писем. Если у тебя возникли проблемы с отправкой письма с сайта, необходимо проверить настройки SMTP-сервера.
