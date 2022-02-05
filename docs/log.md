# Logs -- arquivos de registros

Os arquivos de registro de acesso (*access log* em inglês) do squid encontram-se no arquivo `/var/log/squid/access.log`. Para compreender as entradas do arquivo de log, visite:

- [SquidFaq/SquidLogs - Squid Web Proxy Wiki](https://wiki.squid-cache.org/SquidFaq/SquidLogs)

## Como vejo os arquivos/logs do Squid Log? [^1]

Você pode usar o comando padrão do UNIX/Linux, como `grep`/`tail`, para visualizar os arquivos de log. Você deve efetuar login como *root* ou comando `sudo` para visualizar os arquivos de log.

### Exibição em tempo real dos acessos

Use o comando `tail` de uma das seguintes formas:

- `# tail -f /var/log/squid/access.log`
- `# tail -f /var/log/squid/access.log | ccze`

OU

- `$ sudo tail -f /var/log/squid/access.log`
- `$ sudo tail -f /var/log/squid/access.log | ccze`

### Pesquisa no arquivo de acessos:

Use o comando `grep` da seguinte forma:

- `grep 'texto a pesquisar' /var/log/squid/access.log`

### Visualização do arquivo de registros de acesso

Finalmente, você pode usar o editor de texto como o vi para visualizar os arquivos de log:

- `# view /var/log/squid/access.log`


[^1]: Adaptado de: <https://www.cyberciti.biz/faq/howto-linux-unix-view-squid-log-files/>
