# RSA

En esta sección del repositorio se incluye la implementación del algoritmo RSA, diseñada con fines didácticos, facilitando la comprensión de dicho algoritmo.

Por un lado, se presenta una versión básica del algoritmo desarrollada desde cero, que utiliza números pequeños y no incorpora mecanismos de seguridad adicionales como el padding. Esta implementación permite comprender en detalle cada uno de los pasos del proceso: generación de claves, cifrado y descifrado de mensajes.

Por otro lado, se incluye una segunda versión basada en librerías de criptografía modernas, que implementan RSA de forma completa y segura incluyendo prácticas como el padding o el uso de  claves robustas. El objetivo de esta segunda parte es reflejar cómo es la aplicación de RSA en entornos reales.

<br>

---

## Índice

 - [Configuración](#1)
 - [Instalación y dependencias](#2)
 - [Estructura del proyecto](#3)

<br>

---


## Configuración<a name="1"></a>

A continuación se enumeran los paquetes necesarios para el correcto funcionamiento del programa.

 - Python: 3.10.x
 - [PyCryptodome](https://pypi.org/project/pycryptodome/): 3.23.0

<br>

---

## Instalación y ejecución<a name="2"></a>

1. Clonar el repositorio en su dispositivo local: 
```bash 
git clone https://github.com/pelahumi/Trabajo-de-fin-de-grado.git
```

2. Navegar hasta la carpeta RSA:
```bash
cd Trabajo-de-fin-de-grado/RSA
```

3. Instalar las dependencias: 
```bash
pip install -r requirements.txt
```

4. Ejecutar el programa: 
```bash
python main.py
```

5. Una vez ejecutado el programa, se abrirá un menú donde el usuario puede seleccionar que tipo de versión de RSA quiere ejecutar.

<br>

>  **Advertencia:** Es necesario instalar las dependencias para poder ejecutar la versión avanzada del programa.

<br>

---

## Estructura del proyecto<a name="3"></a>

Como ya se mencionó anteriormente, el proyecto se divide en dos secciones:

### RSA básico

En la carpeta ```Basic_rsa``` se encuentra la estructura de un algoritmo RSA sencillo, desarrollado con el fin de facilitar la comprensión del mismo. El código sigue un enfoque de programación orientada a objetos (POO), donde la clase principal ```RSA``` representa la base del sistema criptográfico.

El cifrado se realiza separando el mensaje por caracteres. De cada caracter se obtiene su valor ASCII para poder aplicar operaciones matemáticas sobre ellos. A continuación se aplica la fórmula de cifrado y se obtiene una lista, donde cada elemento es cifrado correspondiente a cada caracter del mensaje. Para el descifrado, se hace la operación inversa y se juntan los elementos de la lista en un único string.

#### Atributos:

 - p: primer número primo
 - q: segundo número primo
 - N: módulo
 - e: exponente público
 - d: exponente privado
 - phi: funcion de Euler de N

 #### Funcionalidades:

La clase incluye métodos para:

 - Generar las claves púbica y privada
 - Cifrar mensajes
 - Descifrar mensajes

 #### Funciones auxiliares

 Además, se incluye una carpeta auxiliar ```aux``` donde se incluyen funciones auxiliares utilizadas para:

  - ```test_prim.py```: Determinar si un número es primo.
  - ```generate_prim.py```: Generar un número primo entre 100 y 500.
  - ```euler_func.py```: Calcular la función de Euler de N=p*q

### RSA Avanzado

En la carpeta ```Advanced_RSA``` se encuentra la implementación de RSA utilizando la librería ```PyCryptodome```. Esta librería permite aplicar una versión segura y moderna del algoritmo, incluyendo el uso de padding OAEP (Optimal Asymmetric Encryption Padding), así como la codificación del mensaje cifrado en formato ```Base64``` para facilitar su almacenamiento o transmisión.

Gracias a la robustez de esta librería, se garantiza un cifrado mucho más seguro y resistente frente a ataques comunes. Además, permite gestionar claves de tamaño considerable (por ejemplo, 2048 o 4096 bits), lo que mejora significativamente la seguridad frente a la versión básica.

El proceso general seguido en esta implementación es conceptualmente el mismo que en la versión didáctica:

 - Generación de claves RSA con tamaño configurable
 - Cifrado del mensaje con clave pública
 - Descifrado del mensaje con clave privada

> Nota: aunque RSA permite cifrar mensajes directamente, su uso en entornos reales suele combinarse con algoritmos simétricos (AES, por ejemplo) para el manejo eficiente de mensajes largos, esta práctica se conoce como *cifrado híbrido*.