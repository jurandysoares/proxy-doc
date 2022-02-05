# Outras configurações

## apparmor

Perfis do apparmor para o squid. Para maiores informações sobre o apparmor, visite:

- [14.4. Introdução ao AppArmor](https://debian-handbook.info/browse/pt-BR/stable/sect.apparmor.html)
[

Arquivo:

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
    \___/ \/ | \/\/ \/ \___/
    a   b  c d  e f  g   h
    ```

    1. `/etc/`: 
        Diretório de arquivos de configuração do sistema.

    2. `rc`:
        Diretório de recursos (*resources* em inglês).

    3. `2`:
        Nível de execução (*runlevel* em inglês) à qual se refere o diretório.

    4. `.d`:
        Especifica que é um diretório.
        
    5. `S`: indica que o serviço será iniciado (*Started* em inglês) no nível de execução (*runlevel* em inglês) referenciado. Caso o serviço deva ser parado (*Killed* em inglês) no *runlevel*, a letra `K` é utilizada.

    5. `01`:
        Indica a ordem de em que o serviço será parado ou iniciado.

    6. `squid`:
        Especifica o nome do serviço.


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

Arquivo com perfil de configuração para o firewall *ufw*:

- `/etc/ufw/applications.d/squid`

Para maiores informações, visite:

- <https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-18-04-pt>
- <https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands>
