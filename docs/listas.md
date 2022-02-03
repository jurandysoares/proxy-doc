# Listas

Há vários tipos de ACL. Vamos ver as mais simples:

- Por endereço de origem (_source_ em inglês)
- Por endereço de destino (_destination_ em inglês)
- Por domínio de destino (_destination domain_ em inglês)
- Por horário (_time_ em inglês)
  
## Introdução

- As _ACLs (Access Control List)_ são regras para navegação via _proxy_. Elas são lidas na ordem em que aparecem e podem ser combinadas
- A documentação oficial com todas as _ACLs_ pode ser vista em <http://www.squid-cache.org/Doc/config/acl/>.

## Definindo ACL

As _ACLs_ são dispostas das seguintes formas:

```
acl NOME_DA_ACL TIPO_DA_ACL parâmetro
\_/ \_________/ \_________/ \_______/
 1       2           3          4    
```

ou

```
acl NOME_DA_ACL TIPO_DA_ACL '/caminho/completo/regra.conf'
\_/ \_________/ \_________/ \____________________________/
 1       2           3                    4                       
```

- Na primeira forma, será definido todos os parâmetros em sequência separados por espaço, utilizado para regras com poucos parâmetros.
- Na segunda forma, será definido um arquivo para adição dos parâmetros dispostos um por linha, utilizado para regras com muitos parâmetros.
- Todas as _ACLs_ são sensíveis a letras MAIÚSCULAS e minúsculas. Para defini-las como não sensíveis a letras MAIÚSCULAS e minúsculas, utilize a opção `-i` logo após o tipo de _ACL_.

## Conhecendo as ACLs


## REGRAS DAS ACLS

-   http\_access
-   Permite ou nega acessos baseados nas _ACLs_ pré definidas. É utilizado seguido de _allow_ ou _deny_, se a _ACL_ for precedida de um ponto de exclamação significa que será a negação da _ACL_. As regras serão lidas na ordem em que aparecem.

_Segue exemplos_

\# acesso liberado para o diretor baseado em login
http\_access allow DIRETOR

# acesso liberado ao site da integral ecxeto no horário do almoço
http\_access allow SITE\_INTEGRAL !HORARIO\_ALMOCO

# extensão proibida baseado em expressão regular
http\_access deny EXTENSAO\_PROIBIDA

_Após qualquer modificação no arquivo de configuração do **SQUID** faz-se necessário digitar o comando abaixo para que entrem em vigor._

\# squid -k reconfigure

## LOGS

-   _Logs_ do _SQUID_
-   Os _Logs_ de acesso do _SQUID_ encontram-se em **/var/log/squid/access.log**. Para endender a disposição dos _Logs_ acesse o seguinte endereço [http://www.squid-cache.org/Doc/FAQ/FAQ.html#toc6.6](http://www.squid-cache.org/Doc/FAQ/FAQ.html#toc6.6)