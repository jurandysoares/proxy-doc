# Regras

Uma vez definidas as ACLs, podemos aplicar regras a elas. A principal regra é o acesso HTTP, identificado pela diretiva `http_access` [^1], seguido do parâmetro para:

- permitir (*allow* em inglês) ou
- negar (*deny* em inglês)

Se a _ACL_ for precedida de um ponto de exclamação, significa que será a negação da _ACL_. As regras serão lidas na ordem em que aparecem.

## Exemplos

```squid
# acesso liberado para o diretor baseado em login
http_access allow DIRETOR

# acesso liberado ao site da integral exceto no horário do almoço
http_access allow SITE_INTEGRAL !HORARIO_ALMOCO

# extensão proibida baseado em expressão regular
http_access deny EXTENSAO_PROIBIDA
```

Após qualquer modificação no arquivo de configuração do **squid**, é necessário informar o *daemon* [^2] para recarregar reler o o arquivo:  

- `squid -k reconfigure`

Em sistemas baseados em *systemd*, isto pode ser feito executando o comando:

- `systemctl reload squid.service`

[^1]: <http://www.squid-cache.org/Doc/config/http_access/>
[^2]: Serviço no mundo Unix/Linux