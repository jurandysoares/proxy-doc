# Serviço

O serviço do squid, para o systemd, chama-se `squid.service`. Portanto, podemos:

- Iniciá-lo: `systemctl start squid.service`
- Pará-lo: `systemctl stop squid.service`
- Reiniciá-lo: `systemctl restart squid.service`
- Verificarmos estado: `systemctl status squid.service`
- Verificarmos se está ativo: `systemctl is-active squid.service`
- Verificarmos se está habilitado: `systemctl is-enabled squid.service`
- Fazermos ele recarregar o arquivo de configuração: `systemctl reload squid.service`