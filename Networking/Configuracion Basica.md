# Configuración Básica de Networking  

## Nombres de los Dispositivos  

### Cambiar Nombre de Host:  

```plaintext  
Switch# configure terminal  
Switch(config)# hostname Nombre_Dispositivo  
```  

### Para Volver al Nombre Predeterminado:  

```plaintext  
Switch(config)# no hostname  
```  

### Importante:  
- El nombre debe empezar/terminar en letra o número.  
- No debe tener espacios, solo letras, números o guiones.  
- Máximo 63 caracteres.  

## Pautas de Contraseñas  
- Contraseñas largas (>8 caracteres), mezcla de mayúsculas, minúsculas, números y símbolos.  
- No usar contraseñas comunes o iguales en todos los dispositivos.  

## Configuración de Contraseñas  

### Proteger Acceso de Consola:  

```plaintext  
Switch# configure terminal  
Switch(config)# line console 0  
Switch(config-line)# password cisco  
Switch(config-line)# login  
Switch(config-line)# end  
```  

### Proteger Acceso Privilegiado (enable):  

```plaintext  
Switch# configure terminal  
Switch(config)# enable secret class  
Switch(config)# exit  
```  

### Proteger Acceso Remoto (VTY):  

```plaintext  
Switch# configure terminal  
Switch(config)# line vty 0 15  
Switch(config-line)# password cisco  
Switch(config-line)# login  
Switch(config-line)# end  
```  