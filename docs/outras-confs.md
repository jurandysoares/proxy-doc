# Outras configurações

## apparmor

- `/etc/apparmor.d/disable/usr.sbin.squid`
- `/etc/apparmor.d/local/usr.sbin.squid`
- `/etc/apparmor.d/usr.sbin.squid`

## SysVinit

Scripts de gerenciamento do serviço, padrão Init do Sys V. Para maiores informações, visite: <https://guialinux.uniriotec.br/init/> :

- `/etc/init.d/squid`

Scripts de inicialização ou interrupção do serviço, de acordo com o nível de inicialização (*runlevel* em inglês) da máquina:

- `/etc/rc0.d/K01squid`
- `/etc/rc1.d/K01squid`
- `/etc/rc2.d/S01squid`
- `/etc/rc3.d/S01squid`
- `/etc/rc4.d/S01squid`
- `/etc/rc5.d/S01squid`
- `/etc/rc6.d/K01squid`


    Breve comentário sobre o arquivo `/etc/rc2.d/S01squid`:
    ```
    /etc/ rc 2 .d/S 01 squid
    \___/ \/ | \__/ \/ \___/
    a   b  c  d   e   f
    ```

    1. `/etc/`
        Explicação

    2. `rc`
        Explicação

    3. `1`
        Explicação

    4. `.d/K`
        Explicação

    5. `01`
        Explicação

    6. `squid`
        Explicação


## logrotate

Arquivo relacionado à rotação dos arquivos de log do squid:

- `/etc/logrotate.d/squid`

## resolvconf

Arquivo relacionado a resolução de nomes do DNS:

- `/etc/resolvconf/update-libc.d/squid`

## squid

Arquivos específicos de configuração do squid:

- `/etc/squid/conf.d/debian.conf`
- `/etc/squid/errorpage.css`
- `/etc/squid/squid.conf`

## systemd

Arquivo de configuração do serviço para o *systemd*:

- `/etc/systemd/system/multi-user.target.wants/squid.service`

## ufw

Firewall do Ubuntu

- `/etc/ufw/applications.d/squid`
