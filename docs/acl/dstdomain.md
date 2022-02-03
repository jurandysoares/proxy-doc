# ACL de domínio de destino

**dstdomain**

- Trata o domínio de destino solicitado.
- Exemplo:

    ```squid
    acl SITE_INTEGRAL dstdomain .integral.inf.br
    \_/ \___________/ \_______/ \______________/
     a        b           c            d
    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro do tipo de ACL    
