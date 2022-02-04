# ACL de porta

**port**

- Trata a porta de destino da navegação.


- Exemplo:

    ```squid
    acl SITE_8080 port 8080
    \_/ \_______/ \__/ \__/
     a      b      c    d  
    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro do tipo de ACL