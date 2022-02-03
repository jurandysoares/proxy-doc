# ACL de origem

**src**

- Trata o endereço _IP_ ou uma faixa de endereços _IP_ dos dispositivos que acessam o proxy
- Exemplo: 

    ```squid
    acl ESTACAO_DIRETOR src 192.168.1.100/255.255.255.255
    \_/ \_____________/ \_/ \___________________________/
     a         b         c                d
    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro do tipo de ACL
