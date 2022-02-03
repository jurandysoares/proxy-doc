# ACL de tempo

**time**

- Trata um determinado momento baseado em dia da semana e hora.
- Exemplo:

    ```squid
    acl HORARIO_ALMOCO time MTWHF 12:00-14:00
    \_/ \____________/ \__/ \___/ \_________/
     a        b         c     d        e

    ```

    1. Diretiva que indica que uma ACL será definida
    2. Nome da ACL
    3. Tipo da ACL
    4. Parâmetro dias da semana
    5. Parâmetro intervalo de horário

    Segue tabela com abreviação dos dias:

    | Abreviação | Dia da semana | Dia da semana em inglês |
    | :--------: | ------------- | ----------------------- |
    |    `S`     | Domingo       | _Sunday_                |
    |    `M`     | Segunda-feira | _Monday_                |
    |    `T`     | Terça-feira   | _Tuesday_               |
    |    `W`     | Quarta-feira  | _Wednesday_             |
    |    `H`     | Quinta-feira  | _tHursday_              |
    |    `F`     | Sexta-feira   | _Friday_                |
    |    `A`     | Sábado        | _sAturday_              |
