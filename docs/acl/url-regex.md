# ACL de expressão regular na URL

**url_regex**

Trata uma determinada entrada na URL. Pode-se fazer muitas regras baseadas em expressões regulares, porém é preciso conhecer muito bem sobre o assunto.

- Exemplo: 

    ```squid
    acl EXTENSAO_PROIBIDA url_regex -i \.exe$
    \_/ \_______________/ \_______/ \/ \____/
     a          b             c     d    e  
    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Opção que faz a ACL não distinguir letras maiúsculas de minúsculas
    5. Expressão regular que especifica: *terminar com extensão `.exe`*

