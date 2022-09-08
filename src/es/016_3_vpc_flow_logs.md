# VPC Flow Logs

## Introducción

**Los registros de flujo de la VPC** le permiten capturar
**información del tráfico IP** dentro y fuera de la red
Interfaz dentro de su VPC

Los registros de flujo pueden ser creados para

1. VPC
2. Sub-redes
3. Interfaces de red

Todos los datos de registro se **almacenan** utilizando
**Amazon Cloudwatch Logs**. Después de crear un registro de
flujo se puede ver en detalle dentro de CloudWatch Logs

## Definición

```sh
<version> <account-id> <interface-id> <srcaddr> <dstaddr>  <srcport> <dstport> <protocol> <packets> <bytes> <start> <end> <action> <log-states>

# Eg.
# 2 123456789010 eni-abc123de 178.31.16.21 20642 22 6 20 1418530010 141850070 ACCEPT OK
```

- **version** - La versión del registro de flujo de la VPC
- **account-id** - El ID de la cuenta AWS para el
registro de flujo
- **interface-id** - El ID de la interfaz de red para la que
se registra el tráfico
- **srcaddr** - La dirección de origen **IPv4 o IPv6**.
La IPv4 de la interfaz de red es siempre su dirección privada
- **dstaddr** - La **dirección IPv4 o IPv6 de destino**.
El IPv4 de la interfaz de red es siempre su dirección IPv4 privada
- **srcport** - El puerto de origen del tráfico
- **dstport** - El puerto de destino del tráfico
- **protocol** - El número de protocolo IANA del tráfico.
Para más información, consulte Números de protocolo de Internet
asignados
- **packets** - El número de paquetes transferidos durante
la ventana de captura
- **bytes** - El número de bytes transferidos durante
la ventana de captura
- **start** - La hora, en segundos Unix, del inicio de la
la ventana de captura
- **end** - La hora, en segundos Unix, del final de la ventana
de captura la ventana de captura
- **action**
  - ACCEPT: El tráfico registrado fue permitido por
  los grupos de seguridad o ACLs de red
  - RECHAZAR: El tráfico registrado no está permitido por
  los grupos de seguridad o las ACL de red
- **log-status**
  - OK: Los datos se están registrando normalmente en el
  destino elegido
  - NODATA: No hubo tráfico de red hacia o desde
  la interfaz de red durante la ventana de captura
  - SKIPDATA: Se han omitido algunos registros de flujo durante
  durante la ventana de captura. Esto puede deberse a una
  limitaciones de capacidad o un error interno

## Cheat Sheet

- **VPC flow logs** monitoriza el tráfico de entrada y salida
de su Interfaz de red dentro de su VPC
- Puede activar los registros de flujo a nivel de VPC,
sub-red o a nivel de interfaz de red
- Los registros de flujo de la VPC **no pueden ser etiquetados**
como otros recursos de AWS
- Usted **no puede cambiar la configuración** de un
registro de flujo **una vez creado**
- Usted **no puede habilitar** los registros de flujo para las
VPCs que son peered con su VPC
**a menos que esté en la misma cuenta**
- Los registros de flujo VCP pueden ser entregados a
un **S3** o **CloudWatch**.
- Los registros de flujos VCP contienen las
**direcciones IP de origen y destino**
( no el nombre de host )
- Algunos tráficos de instancias **no se supervisan:**
  - Tráfico de instancias generado al contactar con los
  servidores DNS de AWS
  - Tráfico de activación de licencias de Windows desde las instancias
  - Tráfico hacia y desde la dirección de metadatos de la instancia
  ( 169.254.169.254 )
  - Tráfico DHCP
  - Cualquier tráfico hacia la dirección IP reservada de
  el router de la VPC por defecto

<style>
.text-red {
  color: red;
}
</style>
