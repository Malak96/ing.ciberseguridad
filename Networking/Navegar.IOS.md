# Navegación en IOS de Cisco

Para navegar entre los diferentes modos de comandos de un dispositivo Cisco (como un switch o router), usamos varios comandos básicos de IOS.

## Explicación paso a paso

| **Paso**               | **Explicación**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| `enable`               | Entras al modo EXEC privilegiado (el modo donde puedes configurar).             |
| `disable`              | Vuelves al modo EXEC usuario (el modo más básico, sin privilegios de configuración). |
| `configure terminal`   | Entras al modo de configuración global para cambiar la configuración del dispositivo. |
| `exit`                 | Sales de donde estés (por ejemplo, de modo configuración) y subes un nivel.     |
| `line console 0`       | Entras al modo de configuración de la consola (la línea física donde conectas el cable de consola). |
| `line vty 0 15`        | Entras a configurar las líneas VTY (las sesiones remotas por Telnet o SSH).     |
| `interface vlan 1`     | Configuras la interfaz VLAN 1 (normalmente la red de administración del switch). |
| `line console 0` (desde interfaz) | (No es muy común) pero aquí simplemente vuelves a la configuración de consola desde otro modo. |
| `end`                  | Sales directamente de cualquier modo de configuración y regresas al modo EXEC privilegiado. |

## Notas importantes
- **Modo EXEC usuario** (`Switch>`): Es limitado, solo puedes ver información.
- **Modo EXEC privilegiado** (`Switch#`): Te permite ver y configurar.
- **Modo de configuración global** (`Switch(config)#`): Te deja cambiar configuraciones del sistema.
- **Modo de configuración de línea o interfaz** (`Switch(config-line)#`, `Switch(config-if)#`): Es más específico para ciertas partes (líneas, puertos, etc.).
- **Comando `exit`**: Sube un nivel.
- **Comando `end`**: Te lleva directamente al modo EXEC privilegiado (`#`).