# Instalação

- Pacote: `squid`
- Serviço: `squid.service`
- Porta padrão: `3128` (É comum mudar)

Roteiro:

1. Atualizar catálogo: `apt update`
2. Instalar pacote: `apt install -y squid`

## Dados do pacote principal

- Comando: `apt show squid`
- Saída:

    ```yaml
    Package: squid
    Version: 4.10-1ubuntu1.5
    Priority: optional
    Section: web
    Origin: Ubuntu
    Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
    Original-Maintainer: Luigi Gangitano <luigi@debian.org>
    Bugs: https://bugs.launchpad.net/ubuntu/+filebug
    Installed-Size: 8.809 kB
    Provides: squid3
    Pre-Depends: adduser
    Depends: libc6 (>= 2.29), libcap2 (>= 1:2.10), libcom-err2 (>= 1.43.9), libcrypt1 (>= 1:4.1.0), libdb5.3, libecap3 (>= 1.0.1), libexpat1 (>= 2.0.1), libgcc-s1 (>= 3.0), libgnutls30 (>= 3.6.12), libgssapi-krb5-2 (>= 1.17), libkrb5-3 (>= 1.10+dfsg~), libldap-2.4-2 (>= 2.4.7), libltdl7 (>= 2.4.6), libnetfilter-conntrack3 (>= 1.0.7), libnettle7, libpam0g (>= 0.99.7.1), libsasl2-2 (>= 2.1.27+dfsg), libstdc++6 (>= 9), libxml2 (>= 2.7.4), netbase, logrotate (>= 3.5.4-1), squid-common (>= 4.10-1ubuntu1.5), lsb-base, libdbi-perl, ssl-cert
    Recommends: libcap2-bin, ca-certificates
    Suggests: squidclient, squid-cgi, squid-purge, resolvconf (>= 0.40), smbclient, ufw, winbind, apparmor
    Homepage: http://www.squid-cache.org
    Download-Size: 2.562 kB
    APT-Sources: http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
    Description: cache proxy Web repleto de recursos (HTTP proxy)
    Squid é um servidor proxy cache de alta performace para clientes web,
    suportando FTP, gopher, ICY e objetos de dados do HTTP.
    ```

## Pacotes relacionados

- Comando: `apt list squid*`
- Comando: `apt list squid* | cut -d/ -f1`
- Saída:

    ```
    Listing...
    squid-cgi
    squid-common
    squid-deb-proxy-client
    squid-deb-proxy
    squid-langpack
    squid-purge
    squid
    squidclient
    squidguard-doc
    squidguard
    squidtaild
    squidview
    ```

Caso queira descobrir para que serve cada um dos pacotes acima, use o comando:

- `apt show PACOTE`