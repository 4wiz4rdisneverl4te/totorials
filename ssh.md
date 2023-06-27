# SSH

<br>

## 2. Ejemplos

<br>

#### 2.1 Como conectarse por SSH desde un computador A a un computador B

1. Escribir en una terminal del computador A:

    ```
    ssh usuario_computador_B@ip_computador_B
    ```
    
    Por ejemplo, si en el computador B el puerto SSH fue cambiado al 2222:
    
    ```
    ssh -p 2222 usuarioB@192.168.0.10
    ```

<br>

### 2.2 Crear llave SSH

```
ssh-keygen -t ed25519 -a 1000 -f ssh_key_for_xxxx -C user@email.com
```

-t : tipo de encriptación.
-f : nombre del archivo
-a : numero de rondas para descifrar la clave privada. Los números más altos dan como resultado una verificación mas lenta de la contraseña (passphrase) y mayor resistencia al descifrado de contraseñas por fuerza bruta (en caso de robo de las claves). El valor predeterminado es 16 rondas.
-C : comentario, se aconseja la dirección de correo electrónico

<br>

### 2.3 Copiar llave publica (del host) a un servidor

```
ssh-copy-id -i sshkey_for_xxx.pub user@ip
```
-i : nombre de la clave pública (termina en .pub)

<br>

#### 2.4 Como conectarse por SSH desde un computador A a un computador B cuando puerto SSH de computador B no es el predeterminado (22)

1. Escribir en una terminal del computador A:

    ```
    ssh -p puerto_ssh_computador_B usuario_computador_B@ip_computador_B
    ```
    
    Por ejemplo:
    
    ```
    ssh usuarioB@192.168.0.10
    ```

<br>

### 2.4 Tuneles SSH

#### Como conectarse desde un computador A a un puerto del computador C usando un computador B, por ejemplo cuando el computador A y computador C no están en la misma red, pero computador B si puede conectarse a computador A y computador B

Aunque no es relevante, supongamos que dirección ip de computador A es 192.168.100.1, está en la subred 196.168.1.100.0 máscara 255.255.255.0 (misma subred de computador B).

1. En una terminal del computador A escribir:

    ```
    ssh -L puerto_elegido_computador_A:ip_computador_C:puerto_destino_computador_C usuario_en_computador_B@ip_computador_B
    ```

    Por ejemplo, para conectarse a travez del puerto local 20020 del computadorA al puerto 22 (puerto para sesiones SSH) del computadorC:

    ```ssh -L 20022:192.168.200.2:22 usuarioB@192.168.100.2```

    El comando anterior pedirá usualmente contraseña del computador B (usuario usuarioB) y quedará ejecutandose en dicha terminal.

2. Para conectarse por el puerto 20020 del computador A al puerto 22 del computador C (sesión SSH) escribir en otra terminal del computador A:

    ```
    ssh -p puerto_elegido_computador_A usuario_computador_C@localhost
    ```
    
    Por ejemplo:

    ```
    ssh -p 20022 usuario_computador_C@localhost
    ```
    
No solo sirve para sesiones ssh, tambien nos podemos conectar a cualquier otro servicio en cualquier otro puerto

<br>

#### 2.5 Como conectarse desde un computador A a un puerto del computador C y a otro puerto de un computador D usando un computador B, por ejemplo cuando el computador A no está en la misma red del computador C y computador D, pero computador B si puede conectarse a computador A, computador C y computador D (estando computador C y D en misma red o redes diferentes)

Aunque no es relevante, supongamos que dirección ip de computador A es 192.168.100.1, está en la subred 196.168.1.100.0 máscara 255.255.255.0 (misma subred de computador B).

1. Escribir en una terminal del computador A:
    
    ```
    ssh -L puerto_elegido_computador_A:ip_computador_C:puerto_destino_computador_C -L otro_puerto_elegido_computador_A:ip_computador_D:puerto_destino_computador_D  usuario_en_computador_B@ip_computador_B
    ```

    Por ejemplo, para conectarse a travez del puerto local 20020 del computadorA al puerto 22 (puerto para sesiones SSH) del computadorC y del puerto local 13306 del computador A al puerto 3306 del computador D:
    
    ```ssh -L 30022:192.168.200.2:22 -L 13306:192.168.300.3:3306 usuarioB@192.168.100.2```

2. Para conectarse atravez del puerto 30022 del computador A al puerto 22 (sesión SSH) del computador C escribir en otra terminal del computador A:

    ```
    ssh -p puerto_elegido_computador_A usuario_computador_C@localhost
    ```
    
    Por ejemplo:

    ```
    ssh -p 30022 usuario_computador_C@localhost
    ```
    
    Para conectarse atravez del puerto 13306 del computador A a una base de datos en el puerto 3306 (mysql por ejemplo) del computador D escribir en otra terminal del computador A:
    
    ```
    mysql -h 127.0.0.1 -P puerto_elegido_computador_A -u usuario_mysql_del_computador_D -p

    ```
    
    por ejemplo:
    
    ```
    mysql -h 127.0.0.1 -P 13306 -u usuario_mysql -p
    ```

