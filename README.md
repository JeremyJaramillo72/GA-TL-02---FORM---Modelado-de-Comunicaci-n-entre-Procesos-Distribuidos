
# GA-TL-02 — Taller de Modelado de Comunicación entre Procesos Distribuidos

Repositorio correspondiente a la actividad formativa grupal preparatoria para la Práctica Experimental de la Unidad 1 (PE-U1 / GA-SUM-01).

---

## 1. Información Académica e Institucional

- **Institución:** Universidad Técnica Estatal de Quevedo (UTEQ).
- **Facultad:** Facultad de Ciencias de la Ingeniería.
- **Carrera:** Ingeniería de Software.
- **Asignatura:** Aplicaciones Distribuidas (SOF-I-R).
- **Nivel / Paralelo:** 7mo Nivel — Paralelo "A".
- **Docente:** Dr. Gleiston Cicerón Guerrero Ulloa.
- **Período / Semana:** Semana 2 (2 al 8 de noviembre de 2026).
- **Código de Actividad:** GA-TL-02 - FORM.
- **Escenario de Negocio:** Sistema Bancario de Transferencias.

---

## 2. Descripción de la Actividad

El presente proyecto corresponde al taller de modelado de comunicación entre procesos distribuidos, cuyo escenario de negocio es un **Sistema Bancario de Transferencias**.

El objetivo es representar mediante un diagrama la comunicación e interacción entre los diferentes procesos y servicios que intervienen en una transferencia bancaria, identificando los mecanismos de comunicación, protocolos, middleware y características de las interacciones.

El modelo contempla la solicitud de transferencias desde una aplicación de banca móvil o cajero automático (ATM), la validación antifraude, la ejecución de operaciones de débito y crédito, la actualización de cuentas en PostgreSQL y la publicación de eventos para los servicios de notificaciones y auditoría.

Para establecer la comunicación entre los componentes se utilizan mecanismos síncronos y asíncronos, incluyendo REST mediante HTTPS, sockets TCP, RPC mediante gRPC y mensajería mediante AMQP con RabbitMQ.

---

## 3. Integrantes del Equipo de Trabajo

| N.º | Nombres y Apellidos |
|:---:|---|
| 1 | Luis Jeremy Jaramillo Acosta |
| 2 | Kenny Isaías España Vera |
| 3 | Luis Alberto Paca Pilataza |
| 4 | Heiner Ariel Zambrano Ronquillo |

---

## 4. Estructura y Contenido del Repositorio

El repositorio contiene los archivos correspondientes al diagrama de comunicación del Sistema Bancario de Transferencias.

```text
├── README.md
├── diagrama_bancario.drawio
├── Diagrama de Comunicación-Página-1.drawio (4).pdf
└── Diagrama del Sistema Bancario-V1.drawio.png
```

**Descripción de los archivos:**

- `README.md`: documentación general del proyecto, información académica, integrantes e instrucciones de visualización.
- `diagrama_bancario.drawio`: archivo editable original del diagrama de comunicación.
- `Diagrama de Comunicación-Página-1.drawio (4).pdf`: exportación del diagrama en formato PDF.
- `Diagrama del Sistema Bancario-V1.drawio.png`: exportación del diagrama en formato PNG.

---

## 5. Resumen del Modelo de Comunicación entre Procesos

El diseño representa las interacciones entre los componentes del sistema bancario mediante diferentes mecanismos de comunicación:

**1. Cliente (Banca Móvil / ATM) → Servidor de Aplicación**

- **Mecanismo:** Comunicación REST.
- **Protocolo:** HTTPS sobre TCP.
- **Puerto:** 443.
- **Tipo:** Síncrona.
- **Descripción:** El cliente solicita la ejecución de una transferencia al servidor de aplicación.

**2. Servidor de Aplicación ↔ Motor Antifraude**

- **Mecanismo:** Sockets TCP puros.
- **Protocolo:** TCP.
- **Puerto:** 9090.
- **Tipo:** Síncrona.
- **Descripción:** El servidor solicita la validación del riesgo de la transferencia al motor antifraude y espera su respuesta.

**3. Servidor de Aplicación → Servicios de Saldo y Cuentas**

- **Mecanismo:** RPC mediante gRPC.
- **Protocolo:** HTTP/2 y Protocol Buffers.
- **Puerto:** 50051.
- **Tipo:** Síncrona.
- **Descripción:** Se ejecutan las operaciones correspondientes al débito y crédito de las cuentas.

**4. Servicios de Saldo y Cuentas ↔ Base de Datos**

- **Mecanismo:** Comunicación cliente-servidor.
- **Protocolo:** TCP.
- **Puerto:** 5432.
- **Tecnología:** PostgreSQL.
- **Tipo:** Síncrona.
- **Descripción:** Se realizan las operaciones de actualización de cuentas mediante transacciones de base de datos.

**5. Servidor de Aplicación → Broker de Mensajería**

- **Mecanismo:** Mensajería asíncrona.
- **Protocolo:** AMQP 0-9-1.
- **Middleware:** RabbitMQ.
- **Puerto:** 5672.
- **Tipo:** Asíncrona.
- **Descripción:** Se publica un evento de transferencia exitosa para que otros servicios puedan procesarlo.

**6. Broker de Mensajería → Sistema de Notificaciones y Auditorías**

- **Mecanismo:** Mensajería mediante AMQP.
- **Middleware:** RabbitMQ.
- **Tipo:** Asíncrona.
- **Descripción:** El sistema de notificaciones y auditorías consume los eventos publicados por el servidor de aplicación.

---

## 6. Visualización y Edición del Diagrama

El diagrama fue elaborado mediante la herramienta diagrams.net (draw.io). Para visualizarlo o modificarlo se deben seguir los siguientes pasos:

1. Ingresar al sitio web oficial: [diagrams.net](https://app.diagrams.net/).
2. Seleccionar la opción para abrir un diagrama existente.
3. Elegir la opción **Dispositivo (Device)**.
4. Buscar y seleccionar el archivo `diagrama_bancario.drawio`.
5. Una vez abierto, se podrá visualizar y editar el diagrama de comunicación.

También se puede consultar el diseño directamente mediante los archivos PDF y PNG disponibles en el repositorio, sin necesidad de utilizar la herramienta de edición.
