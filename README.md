# CFI-Final
---
Curso: 4º cuatrimestre Ing.Informática
Github: https://github.com/JPabloLobato/CFI-Final.git
---
Índice:
- [Diseño y Modelado de la Arquitectura de Comunicación](#diseño-y-modelado-de-la-arquitectura-de-comunicación)
- [Análisis de Modelos](#análisis-de-modelos)
- [Diseño Lógico y Segmentación](#diseño-lógico-y-segmentación)
- [Capa Física – Cálculos y Selección de Tecnologías](#capa-física-–-cálculos-y-selección-de-tecnologías)
- [Cálculo de la capacidad de los enlaces](#cálculo-de-la-capacidad-de-los-enlaces)
- [Selección de Técnicas de Modulación](#selección-de-técnicas-de-modulación)
- [Evaluación de la Eficiencia del Encapsulamiento](#evaluación-de-la-eficiencia-del-encapsulamiento)
- [Capa de Red – Direccionamiento, Subneteo y Enrutamiento](#capa-de-red-–-direccionamiento-subneteo-y-enrutamiento)
- [Diseño del esquema de direccionamiento IP:](#diseño-del-esquema-de-direccionamiento-ip)
- [Enrutamiento y rutas óptimas:](#enrutamiento-y-rutas-óptimas)
- [Capa de Transporte – Selección de Protocolos y Cálculo del Tamaño de Ventana](#capa-de-transporte-–-selección-de-protocolos-y-cálculo-del-tamaño-de-ventana)
- [Selección de Protocolos de Transporte](#selección-de-protocolos-de-transporte)
- [Cálculo del Tamaño de Ventana en TCP](#cálculo-del-tamaño-de-ventana-en-tcp)
- [Capa de Aplicación – Servicios, Multiplexación y Multimedia](#capa-de-aplicación-–-servicios-multiplexación-y-multimedia)
- [Implementación de Servicios y Resolución de Nombres](#implementación-de-servicios-y-resolución-de-nombres)
- [Servicios Multimedia](#servicios-multimedia)
- [Seguridad – Estrategias y Configuración](#seguridad-–-estrategias-y-configuración)
- [Políticas y Medidas de Seguridad](#políticas-y-medidas-de-seguridad)
- [Cifrado y Autentificación](#cifrado-y-autentificación)
- [Implementación en Cisco Packet Tracer](#implementación-en-cisco-packet-tracer)
- [Construcción de la Topología](#construcción-de-la-topología)
- [Configuración de Protocolos y Servicios](#configuración-de-protocolos-y-servicios)
# Diseño y Modelado de la Arquitectura de Comunicación

## Análisis de Modelos

### Modelo OSI

- **Capa 7: Aplicación**
  - Función: interfaz entre el usuario final y las aplicaciones.
  - Protocolos: HTTP/HTTPS, FTP, SMTP, SNMP, DNS, Telnet.
  - Integración: portales web para los ciudadanos, interfaces de control de tráfico, sistemas de gestión, aplicaciones de monitores ambiental.

- **Capa 6: Presentación**
  - Función: traducción de datos entre formatos ya sea cifrado, descifrado o de compresión o descompresión.
  - Protocolos: SSL/TLS, JPEG, MPEG, ASCII, Unicode.
  - Integración: conversión de formatos para imágenes de videovigilancia, cifrado de datos, compresión de stream.

- **Capa 5: Sesión**
  - Función: establece, administra y finaliza conexiones entre aplicaciones locales y remotas.
  - Protocolos: NetBIOS, RPC, SIP.
  - Integración: gestión de sesiones para videoconferencias, gestión de sesiones para sistemas de control de acceso en edificios públicos.

- **Capa 4: Transporte**
  - Función: segmentación, corrección de errores y control de flujo de extremo a extremo.
  - Protocolos: TCP, UDP.
  - Integración: TCP para transacciones críticas, UDP para streaming de cámaras y sensores IoT.

- **Capa 3: Red**
  - Función: enrutamiento de paquetes, optimización de caminos y direccionamiento lógico.
  - Protocolos: IP (IPv4/IPv6), ICMP, OSPF, BGP.
  - Integración: interconexión entre los diferentes segmentos de la red.

- **Capa 2: Enlace de Datos**
  - Función: acceso al medio, direccionamiento físico (MAC), detección de errores.
  - Protocolos: Ethernet, Wi-Fi, PPP, ATM, Frame Relay.
  - Integración: switches en redes internas, conexión Wi-Fi para ciertos usuarios, enlaces punto a punto entre segmentos de la red.

- **Capa 1: Física**
  - Función: transmisión de bits a través del medio físico.
  - Protocolos: Cables (UTP, fibra óptica), conectores, frecuencia de radio.
  - Integración: cableado de fibra en los edificios y en las ciudades, cableado cat6a en cada para conectar con el dispositivo final y radioenlace entre edificios.

---

### Modelo TCP/IP

- **Capa 4: Aplicación**
  - Función: une la función de las tres capas 5, 6 y 7 de OSI.
  - Protocolos: HTTP, FTP, SMTP, Telnet, SSH, SNMP, DNS.
  - Relación con modelo OSI: combina la interfaz de usuario, representación de datos y control de sesión.
  - Integración: los servicios de aplicación que requieren los diferentes servicios.

- **Capa 3: Transporte**
  - Función: entrega de datos extremo a extremo.
  - Protocolos: TCP y UDP.
  - Relación con modelo OSI: corresponde a la capa de transporte, capa 4.
  - Integración: asegura la fiabilidad en las comunicaciones y la eficiencia en la transmisión.

- **Capa 2: Internet**
  - Función: enrutamiento de datagramas a través de redes.
  - Protocolos: IP, ICMP, IGMP, ARP.
  - Relación con modelo OSI: capa red, capa 3.
  - Integración: enrutamiento entre redes.

- **Capa 1: Acceso de la Red**
  - Función: interfaz con hardware de red y medios físicos.
  - Protocolos: Ethernet, Token Ring, FDDI, Wi-Fi.
  - Relación con modelo OSI: combina las capas Físicas y de Enlace de Datos.
  - Integración: infraestructura física y de enlace que permite la comunicación local y entre ubicaciones.
 ### Diseño Lógico y Segmentación 
 ![](https://github.com/JPabloLobato/CFI-Final/blob/de4d225a84baace13373205d6d02bdeee6dcaa9d/ImagenesDOC/CFI%20FINAL.drawio.png)

---

 # 2. Capa Física – Cálculos y Selección de Tecnologías

## 2.1 Cálculo de la capacidad de los enlaces

### Fórmula de Shannon
C = B * log₂(1 + SNR)

Donde:
- **C** = Capacidad del canal en bits por segundo (bps).
- **B** = Ancho de banda del canal en Hertzios (Hz).
- **SNR** = Relación señal-ruido (debe convertirse de dB a escala lineal).

### Cómo convertir SNR de dB a escala lineal
SNRlineal = 10^(SNR(dB)/10)

### Aplicación a nuestra infraestructura:
- **Para enlaces inalámbricos entre edificios:**
  - B = 80 MHz
  - SNR = 18 dB
  - SNRlineal = 10^(18/10) = 10^1.8 = 63.1
  - Fórmula de Shannon → C = 80,000,000 * log₂(1 + 63.1) = 480,000,000 bps = **480 Mbps**

- **Para enlaces críticos, fibra óptica:**
  - B = 400 MHz
  - SNR = 30 dB
  - SNRlineal = 10^(30/10) = 1000
  - Fórmula de Shannon → C = 400,000,000 * log₂(1 + 1000) = 3,990,000,000 bps = **3.99 Gbps**

- **Para enlaces con cable Cat 6a:**
  - B = 500 MHz
  - SNR = 35 dB
  - SNRlineal = 10^(35/10) = 10^3.5 = 3162.28
  - Fórmula de Shannon → C = 500,000,000 * log₂(1 + 3162.28) = 5,815,000,000 bps = **5.82 Gbps**

---

## 2.2 Selección de Técnicas de Modulación

| Modulación | Bits por símbolo | Eficiencia espectral | Robustez frente a ruido | Aplicaciones adecuadas                       |
|------------|------------------|----------------------|--------------------------|---------------------------------------------|
| **BPSK**   | 1                | Baja                 | Muy alta                 | Enlaces críticos con bastante ruido         |
| **QPSK**   | 2                | Media                | Alta                     | Comunicaciones móviles básicas              |
| **16-QAM** | 4                | Alta                 | Media                    | Wi-Fi, enlaces con buena SNR                |
| **64-QAM** | 6                | Muy alta             | Baja                     | LAN, enlaces con excelente SNR              |
| **256-QAM**| 8                | Extremadamente alta  | Muy baja                 | Fibra óptica, enlaces óptimos               |

### Selección para la infraestructura:

- **Enlaces cableados:**
  - Dentro de edificios: **256-QAM**, debido a su alta eficiencia espectral.
  - Entre edificios cercanos: **16-QAM**, compleja pero con alta velocidad.

- **Enlaces inalámbricos:**
  - **Radioenlaces punto a punto:** **16-QAM**, equilibrio entre velocidad y resistencia a interferencias.
  - **Redes Wi-Fi:** **64-QAM**, alta eficiencia espectral con capacidad de adaptarse a distintas condiciones (puede cambiarse a **BPSK** en condiciones adversas).
  - **Red de IoT:** **QPSK**, gran robustez frente a interferencias externas y adecuada para transmisión de video donde la velocidad es esencial.

---

## 2.3 Evaluación de la Eficiencia del Encapsulamiento

### Ejemplo Práctico: Datos de una cámara de videovigilancia
- **Datos útiles:** 1400 bytes.
- **Sobrecarga por capa:**
  - Capa Aplicación (RTP para video): 12 bytes.
  - Capa Transporte (UDP): 8 bytes.
  - Capa de Red (IPv4): 20 bytes.
  - Capa Enlace (Ethernet): 18 bytes.
  - Preámbulo y delimitadores: 8 bytes.
  - **Total:** 66 bytes.

### Cálculo de la eficiencia:
1. **Tamaño total del paquete:** 1400 + 66 = 1466 bytes.
2. **Eficiencia:** (Datos útiles / Tamaño total) x 100 = (1400 / 1466) x 100 = **95.5%**.

La eficiencia es de un **95.5%**, debido al tamaño de los datos útiles en comparación con la sobrecarga.

---
# 3. Capa de Red – Direccionamiento, Subneteo y Enrutamiento

## 3.1 Diseño del esquema de direccionamiento IP:

| Segmento                          | Bloque de dirección IP | Máscara         | CIDR |
|-----------------------------------|------------------------|-----------------|------|
| Servicios Gubernamentales         | 10.1.0.0              | 255.255.254.0   | /23  |
| Seguridad pública y emergencias   | 10.2.0.0              | 255.255.254.0   | /23  |
| Transporte y monitoreo ambiental  | 10.4.0.0              | 255.255.254.0   | /23  |
| Servicios Multimedia              | 10.3.0.0              | 255.255.254.0   | /23  |
| Gestión y administración de red   | 10.0.254.0            | 255.255.254.0   | /23  |

---

### Cálculos para servicios gubernamentales – 10.0.0.0/24
- **Dirección de red:** 10.0.0.0
- **Dirección broadcast:** 10.0.0.255
- **Rango de direcciones válidas para host:** 10.0.0.1 – 10.0.0.254
- **Número total de hosts disponibles:** 254

---

### Cálculos para seguridad pública – 10.0.1.0/24
- **Dirección de red:** 10.0.1.0
- **Dirección broadcast:** 10.0.1.255
- **Rango de direcciones válidas para hosts:** 10.0.1.1 – 10.0.1.254
- **Número total de hosts disponibles:** 254

---

### Cálculo para transporte y monitoreo – 10.0.2.0/24
- **Dirección de red:** 10.0.2.0
- **Dirección broadcast:** 10.0.2.255
- **Rango de direcciones válidas para hosts:** 10.0.2.1 – 10.0.2.254
- **Número total de hosts disponibles:** 254

---

### Cálculo para servicios multimedia – 10.0.3.0/24
- **Dirección de red:** 10.0.3.0
- **Dirección broadcast:** 10.0.3.255
- **Rango de direcciones válidas para hosts:** 10.0.3.1 – 10.0.3.254
- **Número total de hosts disponibles:** 254

---

### Explicación de por qué la máscara /24
La he elegido por varias razones:
1. Proporciona **254 direcciones IP utilizables** (2^8-2), más que suficiente para los servicios municipales.
2. Limita el tráfico de broadcast a segmentos de un tamaño que se puede administrar con facilidad.

##3.2 Enrutamineto y rutas óptimas:

![](https://github.com/JPabloLobato/CFI-Final/blob/de4d225a84baace13373205d6d02bdeee6dcaa9d/ImagenesDOC/grafo.drawio.png)
