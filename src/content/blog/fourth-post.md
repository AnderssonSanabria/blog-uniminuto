---

title: 'Caso práctico de aplicación'
description: 'Aprende a implementar un sistema básico de cifrado RSA en Java usando NetBeans.'
pubDate: 'Feb 05 2025'
heroImage: '/rsa-java.png'
---

Para ver cómo funciona en la vida real, vamos a usar NetBeans y Java para implementar un sistema básico de cifrado y descifrado con RSA.

```java
import java.security.*;
import javax.crypto.Cipher;

public class RSAExample {
    public static void main(String[] args) throws Exception {
        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
        keyGen.initialize(2048);
        KeyPair pair = keyGen.generateKeyPair();
        
        Cipher cipher = Cipher.getInstance("RSA");
        
        String mensaje = "Hola, este es un mensaje cifrado";
        cipher.init(Cipher.ENCRYPT_MODE, pair.getPublic());
        byte[] cifrado = cipher.doFinal(mensaje.getBytes());
        
        cipher.init(Cipher.DECRYPT_MODE, pair.getPrivate());
        byte[] descifrado = cipher.doFinal(cifrado);
        
        System.out.println("Mensaje original: " + new String(descifrado));
    }
}
```

Este código genera un par de claves, cifra un mensaje con la clave pública y lo descifra con la clave privada.
