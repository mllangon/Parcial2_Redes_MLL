# Parcial2_Redes_MLL

# Examen2_Redes_MLL

# 🛰️ Plan de Direccionamiento IP – Base Eco

**Red base asignada:** `172.16.0.0/24`

Objetivo: subdividir la red para cubrir las necesidades de los departamentos de la Base Eco mediante subnetting.

---

## 🗂️ Requisitos de red

| Departamento            | Hosts necesarios | Subred recomendada | Hosts útiles |
|------------------------|------------------|---------------------|--------------|
| Comando Central        | ~50              | /26                 | 62           |
| Defensa Perimetral     | ~30              | /27                 | 30           |
| Centro Médico          | ~20              | /27                 | 30           |
| Hangar y Taller        | ~14              | /28                 | 14           |
| Enlace Troncal (Antena)| 2                | /30                 | 2            |

---

## 📦 Subredes Asignadas

### 🧠 Comando Central
- Subred: `172.16.0.0/26`
- Rango de hosts: `172.16.0.1` – `172.16.0.62`
- Dirección de broadcast: `172.16.0.63`

### 🛡️ Defensa Perimetral
- Subred: `172.16.0.64/27`
- Rango de hosts: `172.16.0.65` – `172.16.0.94`
- Dirección de broadcast: `172.16.0.95`

### 🏥 Centro Médico
- Subred: `172.16.0.96/27`
- Rango de hosts: `172.16.0.97` – `172.16.0.126`
- Dirección de broadcast: `172.16.0.127`

### 🛠️ Hangar y Taller
- Subred: `172.16.0.128/28`
- Rango de hosts: `172.16.0.129` – `172.16.0.142`
- Dirección de broadcast: `172.16.0.143`

### 📡 Enlace Troncal (Hoth - Galaxia)
- Subred: `172.16.0.144/30`
- Rango de hosts: `172.16.0.145` – `172.16.0.146`
- Dirección de broadcast: `172.16.0.147`

---

## 🧾 Resumen de subredes

+------------------------+---------------------+----------------------------+--------------+
| Departamento           | Subred CIDR         | Rango de IPs               | Hosts útiles |
+------------------------+---------------------+----------------------------+--------------+
| Comando Central        | 172.16.0.0/26       | 172.16.0.1 – 172.16.0.62   | 62           |
| Defensa Perimetral     | 172.16.0.64/27      | 172.16.0.65 – 172.16.0.94  | 30           |
| Centro Médico          | 172.16.0.96/27      | 172.16.0.97 – 172.16.0.126 | 30           |
| Hangar y Taller        | 172.16.0.128/28     | 172.16.0.129 – 172.16.0.142| 14           |
| Enlace Troncal         | 172.16.0.144/30     | 172.16.0.145 – 172.16.0.146| 2            |
+------------------------+---------------------+----------------------------+--------------+

# 🔄 Comparativa: Enrutamiento Estático vs Dinámico

El enrutamiento es el proceso mediante el cual los routers determinan el mejor camino para enviar paquetes de datos a través de una red. Existen dos enfoques principales: **enrutamiento estático** y **enrutamiento dinámico**. A continuación, se detallan sus características, ventajas, desventajas y diferencias clave.

---

## 📌 Enrutamiento Estático

- **Definición**: Las rutas se configuran manualmente por un administrador de red y permanecen fijas hasta que se modifican manualmente.
- **Ventajas**:
  - Simplicidad en redes pequeñas.
  - Menor uso de recursos del router.
  - Mayor seguridad, ya que no se intercambia información de enrutamiento.
- **Desventajas**:
  - No se adapta automáticamente a cambios en la red.
  - Escalabilidad limitada en redes grandes.
  - Mayor carga administrativa para mantener las rutas actualizadas.

---

## 🔁 Enrutamiento Dinámico

- **Definición**: Los routers intercambian información de enrutamiento utilizando protocolos específicos, adaptándose automáticamente a cambios en la topología de la red.
- **Ventajas**:
  - Adaptabilidad a cambios en la red sin intervención manual.
  - Escalabilidad en redes de gran tamaño.
  - Reducción de errores humanos en la configuración de rutas.
- **Desventajas**:
  - Mayor uso de recursos del router (CPU y memoria).
  - Complejidad en la configuración y mantenimiento.
  - Posibles vulnerabilidades si no se implementan medidas de seguridad adecuadas.

---

## 🧭 Protocolos de Enrutamiento Dinámico

### 🛣️ RIP (Routing Information Protocol)

- **Tipo**: Vector de distancia.
- **Funcionamiento**: Utiliza el número de saltos como métrica para determinar la mejor ruta.
- **Características**:
  - Fácil de configurar.
  - Límite máximo de 15 saltos; rutas con más de 15 saltos se consideran inalcanzables.
  - Actualizaciones periódicas cada 30 segundos.
- **Limitaciones**:
  - Convergencia lenta.
  - No considera factores como el ancho de banda o la congestión de la red.

### 🧭 OSPF (Open Shortest Path First)

- **Tipo**: Estado de enlace.
- **Funcionamiento**: Cada router construye una imagen completa de la topología de la red y calcula la ruta más corta utilizando el algoritmo de Dijkstra.
- **Características**:
  - Convergencia rápida.
  - Soporta grandes y complejas redes.
  - Utiliza áreas para segmentar la red y mejorar la eficiencia.
- **Ventajas**:
  - Precisión en la selección de rutas.
  - Mejor adaptación a cambios en la red.

---

## ⚖️ Comparativa: Vector de Distancia vs Estado de Enlace

| Característica             | Vector de Distancia (RIP) | Estado de Enlace (OSPF) |
|----------------------------|---------------------------|-------------------------|
| **Algoritmo**              | Bellman-Ford              | Dijkstra                |
| **Información compartida** | Tablas de rutas completas con vecinos | Información de estado de enlace con todos los routers |
| **Convergencia**           | Lenta                     | Rápida                  |
| **Escalabilidad**          | Limitada                  | Alta                    |
| **Complejidad**            | Baja                      | Alta                    |
| **Uso de recursos**        | Bajo                      | Alto                    |
| **Precisión de rutas**     | Menor                     | Mayor                   |

---

## 📚 Referencias

- [Definición y tipos de enrutamiento dinámico - Universidad VIU](https://www.universidadviu.com/es/actualidad/nuestros-expertos/definicion-y-tipos-de-enrutamiento-dinamico)
- [Estado de enlace - Wikipedia](https://es.wikipedia.org/wiki/Estado_de_enlace)
- [Vector de distancias - Wikipedia](https://es.wikipedia.org/wiki/Vector_de_distancias)

# 🌐 Funcionamiento del Sistema DNS y su Importancia

## 🧠 ¿Qué es el DNS?

El **Sistema de Nombres de Dominio (DNS)** es un componente fundamental de las redes TCP/IP. Su función principal es **traducir nombres de dominio legibles por humanos** (como `rebeldes.org`) en **direcciones IP** que las máquinas necesitan para enrutar correctamente los paquetes (como `192.0.2.1`).

---

## 🔍 ¿Cómo funciona la resolución de nombres?

Cuando un dispositivo (por ejemplo, una terminal en la red rebelde) necesita conectarse a un sitio web o servidor, sigue estos pasos:

1. **Consulta local**:
   - El sistema revisa primero su caché DNS local.
2. **Consulta al servidor DNS configurado**:
   - Si no encuentra la IP localmente, consulta al **servidor DNS** que tiene configurado (generalmente el del router o ISP).
3. **Resolución jerárquica**:
   - El servidor DNS realiza consultas recursivas o iterativas a:
     - **Servidores raíz** (root DNS)
     - **Servidores TLD** (como `.org`, `.com`)
     - **Servidores autoritativos** del dominio
4. **Respuesta final**:
   - Una vez resuelta, la dirección IP se devuelve al cliente, que puede entonces iniciar la conexión TCP/IP con la máquina destino.

---

## 🧾 ¿Qué es un servidor DNS?

Un **servidor DNS** es un dispositivo (o servicio) que:
- Responde a consultas de nombres de dominio.
- Puede actuar como:
  - **Servidor recursivo** (resuelve la consulta completa por el cliente)
  - **Servidor autoritativo** (provee la IP de dominios específicos bajo su control)
  - **Servidor caché** (almacena temporalmente resultados recientes para mejorar rendimiento)

---

## 📌 Tipos de registros DNS

Un **registro DNS** es una entrada en una zona de dominio. Algunos tipos comunes son:

| Tipo de Registro | Descripción                                        | Ejemplo                          |
|------------------|----------------------------------------------------|----------------------------------|
| `A`              | Asocia un dominio a una dirección IPv4            | `rebeldes.org → 192.0.2.1`       |
| `AAAA`           | Asocia un dominio a una dirección IPv6            | `rebeldes.org → 2001:db8::1`     |
| `MX`             | Especifica el servidor de correo para el dominio  | `mail.rebeldes.org`              |
| `CNAME`          | Alias de otro nombre de dominio                    | `www.rebeldes.org → rebeldes.org`|
| `NS`             | Define los servidores DNS autoritativos del dominio| `ns1.rebeldes.org`               |

---

## 🌌 Importancia del DNS en redes como la Rebelde

- **Usabilidad**: Permite a los usuarios usar nombres en lugar de memorizar IPs.
- **Escalabilidad**: Facilita la gestión de miles de dispositivos en red.
- **Flexibilidad**: Cambiar la IP de un servidor no requiere que los usuarios cambien el nombre que utilizan para acceder.
- **Desempeño**: La caché DNS reduce latencia y tráfico innecesario.

---

## 📚 Conclusión

El sistema DNS actúa como la "guía telefónica" de Internet y es esencial para el funcionamiento fluido de cualquier red moderna, incluyendo las redes tácticas como las de la **Alianza Rebelde**. Sin DNS, los usuarios tendrían que recordar direcciones IP, y la escalabilidad de Internet se vería gravemente afectada.

# 🔁 Comparativa entre los protocolos TCP y UDP

En las redes TCP/IP, los protocolos **TCP (Transmission Control Protocol)** y **UDP (User Datagram Protocol)** son fundamentales para la transmisión de datos. Ambos trabajan sobre la capa de transporte del modelo OSI, pero tienen características muy distintas.

---

## 🔐 TCP – Transmission Control Protocol

### 🧩 Características:
- **Orientado a conexión**: Establece una conexión entre el emisor y el receptor antes de transmitir datos (handshake de 3 vías).
- **Confiable**: Garantiza la entrega de todos los paquetes en el orden correcto.
- **Control de flujo y congestión**: Ajusta la velocidad de transmisión según las condiciones de la red.
- **Retransmisión automática**: Reenvía los datos si se detecta pérdida.

### 📦 Ejemplos de uso:
- Navegación web (HTTP/HTTPS)
- Correo electrónico (SMTP, IMAP, POP3)
- Transferencia de archivos (FTP)

### ⚙️ Implicaciones en el rendimiento:
- **Mayor sobrecarga** por los mecanismos de control.
- **Menor velocidad** en redes con muchas interrupciones o alta latencia.
- Ideal cuando **la integridad de los datos es prioritaria**.

---

## 🚀 UDP – User Datagram Protocol

### 🧩 Características:
- **No orientado a conexión**: No establece conexión previa ni garantiza la entrega.
- **No confiable**: No hay confirmación, reenvío ni control de flujo.
- **Ligero y rápido**: Muy poca sobrecarga.

### 📦 Ejemplos de uso:
- Streaming de video/audio (Netflix, YouTube en tiempo real)
- Juegos en línea
- Servicios DNS
- Llamadas VoIP

### ⚙️ Ventajas:
- **Alta velocidad** y menor latencia.
- Adecuado para aplicaciones en tiempo real donde perder algunos paquetes es tolerable.
- Evita retrasos innecesarios por retransmisiones o controles.

---

## ⚖️ Comparativa TCP vs UDP

| Característica         | TCP                             | UDP                          |
|------------------------|----------------------------------|-------------------------------|
| Tipo de conexión       | Orientado a conexión             | Sin conexión                  |
| Confiabilidad          | Alta (garantiza entrega)         | Baja (sin garantía de entrega)|
| Control de flujo       | Sí                               | No                            |
| Orden de los datos     | Garantizado                      | No garantizado                |
| Velocidad              | Menor (más confiable)            | Mayor (menos control)         |
| Uso típico             | Web, email, transferencia segura| Streaming, juegos, VoIP       |

---

## 📚 Conclusión

- **TCP** es ideal cuando se necesita precisión, confiabilidad y control en la transmisión de datos, aunque sacrifique algo de velocidad.
- **UDP** se emplea cuando la **rapidez y baja latencia** son más importantes que la pérdida ocasional de datos, como en streaming o videollamadas.

Ambos protocolos son esenciales y se eligen según el tipo de aplicación y la prioridad entre **rendimiento vs. confiabilidad**.

# 🔁 Comparativa entre los protocolos TCP y UDP (🌌 Edición Galáctica)

En las comunicaciones de la Alianza Rebelde (y cualquier red TCP/IP), **TCP** y **UDP** desempeñan funciones clave. Aquí se explica su funcionamiento y cuándo utilizar cada uno, **con ejemplos aplicados a misiones espaciales**.

---

## 🔐 TCP – Transmission Control Protocol

### 🧩 Características:
- **Orientado a conexión**: Se establece una conexión antes de transmitir datos.
- **Confiable**: Asegura la entrega completa y ordenada.
- **Incluye control de errores, flujo y congestión**.
- **Retransmisión automática** de paquetes perdidos.

### 📦 Ejemplos de uso (Galaxia):
- 📄 **Transmisión de planos estratégicos de la Estrella de la Muerte**
- 🛠️ **Actualizaciones de software de navegación de naves rebeldes**
- 🗳️ **Informes cifrados entre bases rebeldes (como Eco y Yavin IV)**

### ⚙️ Ventajas:
- Ideal para comunicaciones **rutinarias y críticas** donde cada bit importa.
- Evita la pérdida de información clave como coordenadas secretas o códigos de activación.

---

## 🚀 UDP – User Datagram Protocol

### 🧩 Características:
- **No orientado a conexión**
- **No garantiza entrega ni orden**
- **Baja sobrecarga** y **muy rápido**

### 📦 Ejemplos de uso (Galaxia):
- 🎯 **Coordenadas de combate enviadas en tiempo real a escuadrones de X-Wing**
- 📡 **Transmisión de video en vivo desde drones espía en planetas enemigos**
- 📢 **Comandos de emergencia de evacuación rápida**

### ⚙️ Ventajas:
- Permite reacciones rápidas en situaciones de combate.
- **Alguna pérdida de datos es aceptable**, siempre que la mayoría llegue a tiempo.

---

## ⚖️ Comparativa TCP vs UDP

| Característica           | TCP                                            | UDP                                                |
|--------------------------|-------------------------------------------------|-----------------------------------------------------|
| Tipo de conexión         | Orientado a conexión                            | No orientado a conexión                             |
| Confiabilidad            | Alta (garantiza entrega y orden)                | Baja (no hay garantía de recepción ni orden)        |
| Velocidad                | Menor                                           | Mayor                                               |
| Control de flujo/errores| Sí                                              | No                                                  |
| Uso rebelde típico       | Planes estratégicos, datos críticos             | Coordinación de combate, señales de sensores        |

---

## 🧬 Conclusión galáctica

- **TCP** es el protocolo de confianza cuando necesitas **entregar información crítica sin errores**, como los **planos de un arma imperial**.
- **UDP** brilla cuando la **velocidad es clave**, como al transmitir posiciones enemigas a una escuadra de combate que está a segundos de atacar.

En una red rebelde, **ambos protocolos son vitales**: uno para la estrategia, el otro para la acción rápida.

# 🔐 Cifrado Simétrico vs Asimétrico en las Comunicaciones de la Alianza Rebelde

## 🧩 ¿Qué es el cifrado?

El **cifrado** es el proceso de transformar información legible (texto plano) en un formato ilegible (texto cifrado) para proteger su confidencialidad. Solo quienes posean la clave adecuada pueden revertir este proceso y acceder a la información original.

---

## 🔁 Cifrado Simétrico

- **Definición**: Utiliza la **misma clave** para cifrar y descifrar mensajes.
- **Funcionamiento**: Ambas partes deben compartir previamente la clave secreta.
- **Ventajas**:
  - **Rapidez**: Procesamiento más rápido que el cifrado asimétrico.
  - **Eficiencia**: Menor consumo de recursos computacionales.
- **Desventajas**:
  - **Distribución de claves**: Requiere un canal seguro para compartir la clave.
  - **Escalabilidad**: Dificultad para gestionar claves en grandes redes.

**Ejemplo galáctico**:  
Si **Leia** y **Luke** comparten una frase clave secreta para cifrar sus holomensajes, están utilizando **cifrado simétrico**. Ambos deben conocer y proteger esa clave para mantener la seguridad de sus comunicaciones.

---

## 🔐 Cifrado Asimétrico

- **Definición**: Utiliza un par de claves: una **pública** y una **privada**.
- **Funcionamiento**:
  - La clave pública se comparte abiertamente.
  - La clave privada se mantiene en secreto por su propietario.
  - Un mensaje cifrado con la clave pública solo puede ser descifrado con la clave privada correspondiente.
- **Ventajas**:
  - **Seguridad en la distribución de claves**: No es necesario compartir claves secretas.
  - **Autenticación**: Permite verificar la identidad del remitente mediante firmas digitales.
- **Desventajas**:
  - **Rendimiento**: Más lento que el cifrado simétrico.
  - **Complejidad**: Requiere una infraestructura de gestión de claves (PKI).

**Ejemplo galáctico**:  
Si la **Alianza Rebelde** desea enviar un mensaje a un nuevo aliado sin haber intercambiado una clave secreta previamente, puede utilizar **cifrado asimétrico**. El aliado proporciona su clave pública, la Alianza cifra el mensaje con ella, y solo el aliado podrá descifrarlo con su clave privada.

---

## ✅ Autenticación e Integridad: Firma Digital

- **Firma digital**: Mecanismo que permite verificar la **autenticidad** y **integridad** de un mensaje.
- **Funcionamiento**:
  - El remitente genera una firma digital utilizando su clave privada.
  - El receptor verifica la firma con la clave pública del remitente.
- **Beneficios**:
  - **Autenticación**: Confirma la identidad del remitente.
  - **No repudio**: El remitente no puede negar haber enviado el mensaje.
  - **Integridad**: Asegura que el mensaje no ha sido alterado durante la transmisión.

**Ejemplo galáctico**:  
Al recibir un mensaje firmado digitalmente, la **Alianza Rebelde** puede estar segura de que proviene realmente de **Leia** y que no ha sido modificado por el Imperio durante su transmisión.

---

## 🛡️ Importancia de Protocolos Seguros: SSH vs Telnet

- **Telnet**:
  - Transmite datos en texto plano.
  - Vulnerable a interceptaciones y ataques.
- **SSH (Secure Shell)**:
  - Cifra toda la comunicación.
  - Proporciona autenticación y seguridad en el acceso remoto.

**Ejemplo galáctico**:  
Al administrar remotamente los sistemas de la **Base Eco**, es crucial utilizar **SSH** en lugar de **Telnet** para evitar que el Imperio intercepte credenciales o comandos sensibles.

---

## 🧬 Conclusión

- **Cifrado simétrico**: Eficiente para comunicaciones entre partes que ya comparten una clave secreta.
- **Cifrado asimétrico**: Ideal para establecer comunicaciones seguras sin necesidad de compartir previamente una clave secreta.
- **Firma digital**: Esencial para garantizar la autenticidad e integridad de los mensajes.
- **Protocolos seguros**: Herramientas como **SSH** son fundamentales para proteger las operaciones y comunicaciones de la Alianza Rebelde frente a amenazas del Imperio.

---

## 📚 Referencias

- [Cifrado (criptografía) - Wikipedia](https://es.wikipedia.org/wiki/Cifrado_%28criptograf%C3%ADa%29)
- [Firma digital - Wikipedia](https://es.wikipedia.org/wiki/Firma_digital)
- [Seguridad de la información - Wikipedia](https://es.wikipedia.org/wiki/Seguridad_de_la_informaci%C3%B3n)
