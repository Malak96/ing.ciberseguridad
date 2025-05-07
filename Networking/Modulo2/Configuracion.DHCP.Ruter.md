## Configuración de DHCP en un Router Cisco `GIA`

Esta configuración es para un router Cisco con IOS, y permite:

- Configurar una interfaz de red.
- Crear un servidor DHCP interno.
- Excluir algunas direcciones IP del rango que entregará el DHCP.

---

### 1. Configuración de la interfaz GigabitEthernet0/0 (G0/0)

```plaintext
Router0(config)# int Gi0/0
Router0(config-if)# ip add 172.16.0.1 255.255.0.0
Router0(config-if)# no shut
```

#### ¿Qué hace?

- **int Gi0/0**: Entra en la configuración de la interfaz física GigabitEthernet 0/0.
- **ip add 172.16.0.1 255.255.0.0**: Asigna a esa interfaz la IP `172.16.0.1` con máscara de 16 bits (`255.255.0.0`), es decir, una red grande (65,534 hosts posibles).
- **no shut**: Activa la interfaz (por defecto, una interfaz nueva en Cisco está administrativamente apagada).

**Resumen**: Se asigna al router una IP propia en la red `172.16.0.0/16`.

---

### 2. Creación de un Pool DHCP llamado `DHCP-POOL-01`

```plaintext
Router0(config)# ip dhcp pool DHCP-POOL-01
Router0(dhcp-config)# default-router 172.16.0.1
Router0(dhcp-config)# dns-server 172.16.0.1
Router0(dhcp-config)# network 172.16.0.0 255.255.0.0
Router0(dhcp-config)# exit
```


```plaintext
Router0(config)# ip dhcp excluded-address 172.16.0.1 172.16.0.99
```

#### ¿Qué hace?

- **ip dhcp excluded-address 172.16.0.1 172.16.0.99**: Indica que las direcciones IP desde `172.16.0.1` hasta `172.16.0.99` no deben ser asignadas por el servidor DHCP.

Esto es importante porque:

- `172.16.0.1` es usada por el propio router.
- Las direcciones entre `172.16.0.2` y `172.16.0.99` pueden ser necesarias para dispositivos configurados manualmente, como servidores o impresoras.


### Resumen de todo 


| **Concepto**              | **Valor**                      | **Comando usado**                                                                 | **Descripción**                                                                 |
|---------------------------|--------------------------------|------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| IP de la interfaz         | 172.16.0.1                     | `interface vlan 1`<br>`ip address 172.16.0.1 255.255.0.0`                          | Asigna IP y máscara a la interfaz virtual VLAN 1 (administración del switch).         |
| Máscara de red            | 255.255.0.0 (o /16)            | Incluida en `ip address 172.16.0.1 255.255.0.0`                                    | Define el tamaño de la red (en este caso, clase B).                                   |
| Red configurada           | 172.16.0.0/16                  | Derivada de la IP y máscara                                                       | Se obtiene automáticamente a partir de IP y máscara asignadas.                        |
| Default Gateway (DHCP)    | 172.16.0.1                     | `ip dhcp pool <nombre>`<br>`default-router 172.16.0.1`                             | Establece la puerta de enlace que recibirán los clientes DHCP.                        |
| DNS Server (DHCP)         | 172.16.0.1                     | `ip dhcp pool <nombre>`<br>`dns-server 172.16.0.1`                                 | Establece el servidor DNS que recibirán los clientes.                                 |
| IPs excluidas del DHCP    | 172.16.0.1 a 172.16.0.99       | `ip dhcp excluded-address 172.16.0.1 172.16.0.99`                                  | Evita que esas IPs sean asignadas por el DHCP; se reservan para uso manual.           |
| Rango de IPs para DHCP    | 172.16.0.100 en adelante       | `ip dhcp pool <nombre>`<br>`network 172.16.0.0 255.255.0.0`                        | Define el rango de direcciones IP que se entregarán a los clientes DHCP.              |



### Notas Adicionales

### ¿Qué es exactamente la Default Gateway?

La Default Gateway es el dispositivo que sabe hacia dónde enviar los paquetes cuando el destino está fuera de la red local.
Es como la "puerta de salida" de tu red.

- Si un dispositivo quiere comunicarse con algo dentro de su misma red, no usa la Gateway.
- Si quiere comunicarse con otra red (por ejemplo, salir a internet o a otra subred), **sí necesita** enviar los paquetes a la **Default Gateway**.