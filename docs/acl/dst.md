# ACL de destino

**dst**

- Trata o endereço _IP_ ou uma faixa de endereços _IP_ dos destinos solicitados
- Exemplo:

    ```squid
    acl IP_INTEGRAL dst 200.175.44.1/255.255.255.255
    \_/ \_________/ \_/ \__________________________/
     a       b       c               d
    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro do tipo de ACL    
