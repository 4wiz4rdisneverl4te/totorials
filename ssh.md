# SSH

## Ejemplos

### Conexiones básicas

#### Como conectarse por SSH desde un computador A a un computador B

1. Escribir en una terminal del computador A:

    ```
    ssh usuario_computador_B@ip_computador_B
    ```
    
    Por ejemplo:
    
    ```
    ssh usuarioB@192.168.0.10
    ```

### Tuneles SSH

#### Como conectarse desde un computador A a un puerto del computador C usando un computador B, por ejemplo cuando el computador A y computador C no están en la misma red, pero computador B si puede conectarse a computador A y computador B

1. En una terminal del computador A escribir:

    ```
    ssh -L puerto_elegido_computador_A:ip_computador_C:puerto_destino_computador_C usuario_en_computador_B@ip_computador_B
    ```

    Por ejemplo, si deseo conectarme a travez del puerto local 20020 del computadorA al puerto 22 (puerto para sesiones SSH) del computadorC:

    ```ssh -L 20022:192.168.200.2:22 usuarioB@192.168.100.2```

    El comando anterior pedirá usualmente contraseña del computador B (usuario usuarioB) y quedará ejecutandose en dicha terminal.

2. Escribir en otra terminal del computador A escribir:

    ```
    ssh -p puerto_elegido_computador_A usuario_computador_C@localhost
    ```
    
    Por ejemplo, continuando la implementacion del punto 1, nos conectemonos del computador A al C por medio de una sesión ssh:

    ```
    ssh -p 20022 usuario_computador_C@localhost
    ```
    
No solo sirve para sesiones ssh, tambien nos podemos conectar a cualquier otro servicio en cualquier otro puerto

#### Como conectarse desde un computador A a un puerto del computador C y a otro puerto de un computador D usando un computador B, por ejemplo cuando el computador A no está en ña misma red del computador C y computador Dno están en la misma red, pero computador B si puede conectarse a computadorA, computador C y computador D


1. Escribir en una terminal del computador A:
    
    ```
    ssh -L puerto_elegido_computador_A:ip_computador_C:puerto_destino_computador_C -L otro_puerto_elegido_computador_A:ip_computador_D:puerto_destino_computador_D  usuario_en_computador_B@ip_computador_B
    ```

    Por ejemplo, si deseo conectarme a travez del puerto local 20020 del computadorA al puerto 22 (puerto para sesiones SSH) del computadorC:

2. En otra terminal del computador A escribir: por ejemplo, si nos queremos conectar atravez del puerto 30022 del computador A al puerto 22 del computador C y atravez del puerto 13306 a una base de datos en el puerto 3306 del computador D hariamos lo siguiente:

