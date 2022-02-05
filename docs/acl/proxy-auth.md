# ACL de autenticação do proxy

**proxy_auth**

-  Trata o _Login_ com que o cliente se autentica no _Proxy_. Requer uma configuração de autenticação.

- Exemplo:

    ```squid
    acl DIRETOR proxy_auth joao
    \_/ \_____/ \________/ \__/
     a     b        c       d  
    ```
    
    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro do tipo de ACL 
