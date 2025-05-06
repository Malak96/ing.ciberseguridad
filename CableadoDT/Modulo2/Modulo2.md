# Unidad 2: Redes y Monitoreo

**Temas:**

* Redes tradicionales
* Redes definidas por software (SDN)
* Red de Data Center
* Monitoreo de infraestructura y servidores

---

## Redes Tradicionales

Una red tradicional es aquella en la que la infraestructura de comunicaciones se basa en dispositivos de hardware (switches, routers, firewalls), los cuales son gestionados y configurados de forma manual e individual. En este tipo de red, el plano de control (responsable de tomar decisiones de tráfico) y el plano de datos (responsable de mover los datos) residen conjuntamente en cada dispositivo.

**Principales características:**

* **Gestión manual:** La administración de la red implica acceder a cada equipo de forma separada para realizar configuraciones o actualizaciones.
* **Dependencia de hardware propietario:** Se utilizan dispositivos específicos de fabricantes determinados, con poca flexibilidad para la integración tecnológica de otros proveedores.
* **Escalabilidad ajustada:** A medida que el tamaño de la red crece, la complejidad de su gestión también aumenta, volviéndose más propensa a errores humanos.
* **Adaptación lenta al cambio:** La implementación de modificaciones o nuevas políticas de red requiere un proceso manual y repetitivo en múltiples equipos.

**Arquitectura:** Basada en hardware con configuración manual.
**Control:** Distribuido en cada equipo de red.
**Escalabilidad y automatización:** Limitadas.
**Uso común:** Oficinas pequeñas o redes convencionales.

---

## Redes Definidas por Software (SDN)

Arquitectura de red que separa el plano de control (decisiones de tráfico) del plano de datos (transporte de paquetes), permitiendo una gestión centralizada y automatizada mediante un controlador de red.

**Ventajas:**

* Simplifica la administración de grandes infraestructuras.
* Permite programación dinámica de la red.
* Mejora la agilidad, escalabilidad y optimización de costos.

**Ejemplos de uso:**

* Data centers que requieren rápido aprovisionamiento de servicios.
* Redes de nube pública/privada para balanceo dinámico de cargas.
* Entornos de investigación y educación que requieren redes flexibles.
* Proveedores de servicios (ISP) para gestionar redes WAN de forma eficiente.

**Administración:** Centralizada mediante software.
**Tecnologías:** OpenFlow, Cisco ACI, VMware NSX.

---

## Red Data Center

Una Red de Data Center es la infraestructura de comunicación que conecta los servidores, dispositivos de almacenamiento, servicios de red y sistemas de monitoreo dentro de un centro de datos.

Su función principal es asegurar el flujo eficiente, confiable y seguro de la información entre todos los componentes internos y hacia el exterior.

---

## Características principales de las Redes (Aplicables a diferentes tipos):

* **Alta Disponibilidad:** La red debe minimizar tiempos de caída mediante redundancia en enlaces y dispositivos.
* **Baja Latencia:** Crucial para servicios sensibles al tiempo, como aplicaciones financieras, bases de datos y servicios en tiempo real.
* **Flexibilidad:** Adaptable a arquitecturas virtualizadas y a entornos de nube híbrida o privada.
* **Seguridad:** Segmentación de tráfico, control de acceso, firewalls internos y monitoreo constante.

---

## Componentes esenciales de las Redes de Data Center:

* **Core Layer:** Núcleo de alta velocidad que interconecta todas las capas.El núcleo: transporta datos rápidamente entre zonas **(Switches de alta velocidad, sin políticas).**

* **Aggregation (Distribution) Layer:** Consolida tráfico de los switches de acceso y aplica políticas de seguridad y enrutamiento **(Switches con funciones de enrutamiento + Firewalls + Load Balancers)**.

* **Access Layer:** Conecta directamente a los servidores, almacenamiento y otros dispositivos. **(Switches que conectan PCs, servidores, almacenamiento, etc.)**

---

## Topologías comunes:

* **Red de tres capas (Tradicional, jerárquica):**
    * Modelo de red jerárquico clásico.
    * Compuesto por tres capas funcionales:
        * **Core Layer:** Encargada del transporte de alto rendimiento y conectividad entre distintos bloques de red.
        * **Distribution Layer (Agregación):** Aplica políticas de seguridad, filtrado y enrutamiento; sirve como intermediario entre la capa de acceso y el core.
        * **Access Layer:** Donde se conectan directamente los servidores, estaciones de trabajo y otros dispositivos finales.
    * **Ventaja:** Diseño modular, organizado y fácil de mantener.
    * **Limitación:** Puede generar cuellos de botella en tráfico lateral (entre servidores).

* **Topología Leaf-Spine (Moderna, optimizada para tráfico este-oeste entre servidores):**
    * Arquitectura de red plana y escalable, ideal para data centers modernos.
    * Consta de dos niveles:
        * **Leaf switches:** Conectan directamente a servidores y dispositivos.
        * **Spine switches:** Interconectan todos los leafs entre sí.
    * **Ventaja principal:** Optimiza el tráfico este-oeste (entre servidores) con rutas equidistantes y balanceadas, reduciendo la latencia.
    * **Uso común:** Data centers virtualizados, servicios en la nube, redes SDN.

---

## Ejemplos de uso

* Data centers que requieren rápido aprovisionamiento de servicios.
* Redes de nube pública/privada para balanceo dinámico de cargas.
* Entornos de investigación y educación que requieren redes flexibles.
* Proveedores de servicios (ISP) para gestionar redes WAN de forma eficiente.
* Data centers de servicios de nube (como Amazon Web Services o Microsoft Azure) emplean redes de alta capacidad y baja latencia para gestionar millones de conexiones simultáneas.

---

## Monitoreo de infraestructura y servidores

**Sistemas de Monitoreo:**

Monitorean recursos físicos y virtuales. Detectan fallos, analizan tendencias y optimizan capacidad.

**Parámetros:** CPU, RAM, red, temperatura, energía.

**Ejemplos:** Zabbix, PRTG, Prometheus + Grafana, Librenms.

---

## Herramientas de Monitoreo:

| Herramienta         | Monitorea principalmente               | Ideal para                                     | Características destacadas                                                                                                                               |
| :------------------ | :------------------------------------- | :--------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Zabbix** | Recursos físicos, red, aplicaciones    | Redes corporativas tradicionales               | Monitoreo en tiempo real, alertas automáticas y generación de reportes. Muy utilizado en redes corporativas y data centers medianos o grandes. Monitoriza recursos de servidores (CPU, memoria, uso de disco, procesos), equipos de red (switches, routers, firewalls - estado de puertos, tráfico, latencia), aplicaciones (bases de datos, servidores web, servicios críticos), sensores de ambiente (temperatura, humedad, energía). |
| **PRTG MInnitor** | Infraestructura completa, tráfico, cloud | Redes híbridas (físico, virtual, nube)         | Monitoreo integral (supervisión de toda la infraestructura), Dashboard interactivo (visualización intuitiva), Alertas automáticas (notificaciones en tiempo real), Generación de informes (reportes detallados). Monitorea estado de enlaces (ancho de banda, calidad, pérdida de paquetes), bases de datos, servidores de correo, almacenamiento, sensores virtuales personalizados para medir cualquier tipo de dato. |
| **Prometheus + Grafana** | Métricas de sistemas, aplicaciones, microservicios | Entornos dinámicos, virtualizados, DevOps    | Prometheus recolecta y almacena métricas. Grafana visualiza datos de Prometheus mediante dashboards personalizables. Ideal para entornos dinámicos, virtualizados, de alta automatización. Monitorea servicios en la nube, contenedores (Docker, Kubernetes), microservicios, y hardware de servidores si se integran exporters. |
| **LibreNMS** | Equipos de red, servidores físicos, sensores SNMP | Redes medianas y grandes basadas en SNMP       | Basado en SNMP (protocolo de monitoreo estándar). Detección automática de dispositivos y topologías de red. Soporte para alertas (integración de notificaciones: correo, Slack, etc.). Solución de código abierto altamente personalizable. Monitoriza equipos de red (switches, routers, firewalls), servidores físicos y virtuales (estado de CPU, memoria, almacenamiento), sensores de hardware (energía, temperatura, ventiladores). |