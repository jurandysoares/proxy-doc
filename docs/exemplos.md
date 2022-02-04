# Exemplo

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