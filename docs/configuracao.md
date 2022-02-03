# Configuração

## Diretório e arquivos de configuração

- Diretório: `/etc/squid/`
- Arquivo principal: `/etc/squid/squid.conf`

Quantas linhas tem o arquivo principal de configuração?

- Comando: `wc -l /etc/squid/squid.conf`
- Saída: `8586 /etc/squid/squid.conf`

Seria viável decifrar estas 8.000 e tantas linhas?

Para nosso consolo, a maioria delas é de comentários ou linhas em branco. 
Podemos facilmente _limpar_ o arquivo utilizando o editor `sed`. Seguem comandos para exercitar:

1. `sed '/^#/d' /etc/squid/squid.conf`
2. `sed '/^$/d' /etc/squid/squid.conf`
3. `sed '/^#/d;/^$/d' /etc/squid/squid.conf`

O comando *1* apaga as linhas com comentários, o *2* apaga as linhas em branco e o comando *3* faz a mesma coisa que os comandos 1 e 2 combinados. Por padrão, o comando `sed` exibe na saída padrão (no terminal) o resultado da edição. Para salvar as alterações no arquivo original, passe a opção `-i`:

- `sed -i '/^#/d;/^$/d' /etc/squid/squid.conf`

O arquivo resultante deve ficar mais ou menos assim:

```squid
acl localnet src 0.0.0.1-0.255.255.255	# RFC 1122 "this" network (LAN)
acl localnet src 10.0.0.0/8		# RFC 1918 local private network (LAN)
acl localnet src 100.64.0.0/10		# RFC 6598 shared address space (CGN)
acl localnet src 169.254.0.0/16 	# RFC 3927 link-local (directly plugged) machines
acl localnet src 172.16.0.0/12		# RFC 1918 local private network (LAN)
acl localnet src 192.168.0.0/16		# RFC 1918 local private network (LAN)
acl localnet src fc00::/7       	# RFC 4193 local private network range
acl localnet src fe80::/10      	# RFC 4291 link-local (directly plugged) machines
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost manager
http_access deny manager
include /etc/squid/conf.d/*
http_access allow localhost
http_access deny all
http_port 3128
coredump_dir /var/spool/squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern \/(Packages|Sources)(|\.bz2|\.gz|\.xz)$ 0 0% 0 refresh-ims
refresh_pattern \/Release(|\.gpg)$ 0 0% 0 refresh-ims
refresh_pattern \/InRelease$ 0 0% 0 refresh-ims
refresh_pattern \/(Translation-.*)(|\.bz2|\.gz|\.xz)$ 0 0% 0 refresh-ims
refresh_pattern .		0	20%	4320
```

Observe que da linha 1 à linha 20 são definidas listas de controle de acesso (ACL na sigla em inglês).

E nas linhas da 21 à 28 o acesso HTTP é permitido (*allow* em inglês) ou negado (*deny* em inglês).

A configuração básica do squid consiste em:

1. Definir listas de controles de acesso
2. Permitir ou negar acesso HTTP para as ACLs definidas no passo anterior
3. Reiniciar o serviço
4. Acompanhar ou analisar os arquivos de log de acesso do squid

