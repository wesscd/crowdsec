
# Instalação CrowdSec no pfSense. #

"A liberdade é a possibilidade de autodomínio; de não ser escravo das próprias paixões e impulsos, mas de seguir a razão."
Kant

### Compilação feita baseado na documentação oficial. ###

Os comandos abaixo são feitos com os links do [git official do CrowdSec](https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/)

```shell
pkg add -f <link to abseil>
pkg add -f <link to re2>
pkg add -f <link to crowdsec-firewall-bouncer>
pkg add -f <link to crowdsec>
pkg add -f <link to pfSense-pkg-crowdsec>
```

Então os comandos sairiam assim:

```shell
pkg add -f https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/download/v0.1.2/abseil-20230125.3.pkg
pkg add -f https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/download/v0.1.2/re2-20231101.pkg
pkg add -f https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/download/v0.1.2/crowdsec-firewall-bouncer-0.0.28_1.pkg
pkg add -f https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/download/v0.1.2/crowdsec-1.5.6.r8_1.pkg
pkg add -f https://github.com/crowdsecurity/pfSense-pkg-crowdsec/releases/download/v0.1.2/pfSense-pkg-crowdsec-0.1.2.pkg

```
Faz o registro de uma conta para o uso da API:
![enter image description here](https://i.imgur.com/F6imrGH.png)


Após registro, colete a API Key(Click em copy):

![enter image description here](https://i.imgur.com/hZG39pD.png)

Execute na sequencia abaixo:

1
```shell
cscli capi register
```
2
```shell
cscli console enroll -e context cm1gq65eq0007lber22iuy321
```
3
Habilitar os serviços.
```shell

sysrc crowdsec_enable="YES"
sysrc crowdsec_firewall_enable="YES"

```
4
Executar os serviços.
```shell
service crowdsec start
service crowdsec_firewall start
```

