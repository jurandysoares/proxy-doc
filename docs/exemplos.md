# Exemplos

Exemplo de configuração para arquivo `/etc/squid/squid.conf` [^1]:

```squid
acl rede_local src 192.168.0.0/24
acl palavras_bloqueadas url_regex -i "/etc/squid/palavras_bloqueadas.txt"
acl sites_bloqueados url_regex -i "/etc/squid/ sites_bloqueados.txt "
acl redes_sociais url_regex -i "/etc/squid/redes_sociais.txt"
acl liberados src "/etc/squid/ips_liberados.txt "
acl porno url_regex -i "/etc/squid/sites_porno.txt "
acl formato_arquivo url_regex -i "/etc/squid/formato_arquivo.txt"
acl horario_almoco time 12:00-13:00

http_access allow liberados
http_access allow redes_sociais  horario_almoco
http_access deny redes_sociais
http_access deny sites_bloqueados
http_access deny palavras_bloqueadas
http_access deny porno
http_access deny formato_arquivo
http_access allow rede_local
```

[^1]: Exemplo extraído e adaptado de <https://docente.ifrn.edu.br/filiperaulino/disciplinas/seguranca-de-redes/aulas/Aula%20extra%20squid.pdf>

---

## Exemplo com bloqueio de redes sociais e de arquivos de vídeo

Arquivo `/etc/squid/squid.conf`:

```squid
acl vbox_host_only src 192.168.56.0/24
acl servidores src 192.168.56.10-192.168.56.30
acl unicamp dst 143.106.0.0/16
acl redes_sociais dstdomain "/etc/squid/redes-sociais.conf"
acl horario_almoco time MTWHF 12:00-14:00
acl extensoes_filmes url_regex -i "/etc/squid/filmes.conf"
acl site_8080 port 8080


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

http_access allow servidores
http_access allow redes_sociais horario_almoco  # Rede social liberada só no horário de almoço
http_access deny extensoes_filmes # Bloquear download de filmes
http_access deny redes_sociais # Bloquear redes sociais
http_access allow vbox_host_only # Permitir acessos da rede host-only do VirtualBox

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

Arquivo `/etc/squid/filmes.conf`:

```
\.mp4$
\.avi$
```

Arquivo `/etc/squid/redes-sociais.conf`:

```
.facebook.com
.twitter.com
.tiktok.com
.instagram.com
```