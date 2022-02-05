# Listas de controle de acesso (ACLs)

Há vários tipos de ACL. Vamos ver as mais simples:

- Por endereço de origem (_source_ em inglês)
- Por endereço de destino (_destination_ em inglês)
- Por domínio de destino (_destination domain_ em inglês)
- Por horário (_time_ em inglês)
- Expressão regular da URL (_url regex_ em inglês)
- Porta (_port_ em inglês)
- Autenticação (_auth_ em inglês)
  
## Introdução

- As _ACLs (Access Control List)_ são regras para navegação via _proxy_. Elas são lidas na ordem em que aparecem e podem ser combinadas
- A documentação oficial com todas as _ACLs_ pode ser vista em:

    -  <http://www.squid-cache.org/Doc/config/acl/>.

## Definindo ACL

Trecho extraído da [documentação oficial sobre ACLs](http://www.squid-cache.org/Doc/config/acl/):

```
Defining an Access List

	Every access list definition must begin with an aclname and acltype, 
	followed by either type-specific arguments or a quoted filename that
	they are read from.

	   acl aclname acltype argument ...
	   acl aclname acltype "file" ...
```

As _ACLs_ são dispostas das seguintes formas:

```squid
acl NOME_DA_ACL TIPO_DA_ACL argumento
\_/ \_________/ \_________/ \_______/
 1       2           3          4    
```

ou

```squid
acl NOME_DA_ACL TIPO_DA_ACL "/caminho/completo/regra.conf" 
\_/ \_________/ \_________/ \____________________________/
 1       2           3                    4                       
```

- Na primeira forma, serão definidos todos os parâmetros em sequência, separados por espaço. É utilizada para regras com poucos parâmetros.
- Na segunda forma, será definido um arquivo para adição dos parâmetros dispostos um por linha. É utilizada para regras com muitos parâmetros.
- Todas as _ACLs_ são sensíveis a letras MAIÚSCULAS e minúsculas. Para defini-las como não sensíveis a letras MAIÚSCULAS e minúsculas, utilize a opção `-i` logo após o tipo de _ACL_. Veja trecho extraído e traduzido de: <http://www.squid-cache.org/Doc/config/acl/>:
  
> `-i`, `+i`  Por padrão, expressões regulares (regex [^1]) são sensíveis a letras MAIÚSCULAS e minúsculas. Para torná-las insensíveis a letras maiúsculas ou minúsculas, use a opção `-i`. Para retornar a sensibilidade a letras MAIÚSCULAS e minúsculas, use a opção `+i` entre os padrões ou crie uma nova linha de ACL sem a opção `-i`.


[^1]: *Regular expressions* em inglês, e comumente abreviada como *regex* ou *re*. Por exemplo, o módulo de Python para expressões regulares se chama *re* (<https://docs.python.org/pt-br/3/library/re.html>). Um tutorial de como usar expressões regulares em Python pode ser lido em: <https://docs.python.org/pt-br/3/howto/regex.html>.
