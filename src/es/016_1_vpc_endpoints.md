# VPC Endpoints

Piensa en un túnel secreto en el que no tienes que salir de
la red de AWS

## Introducción

Los **VPC Endpoint** le permiten
**conectar de forma privada su VPC a otros servicios de AWS**,
y los servicios de VPC endpoint

<img
  src="../../public/images/vpc/endpoints.png"
  alt="VPC Endpoints" />

Existen **2 tipos** de puntos finales de la VPC

1. Endpoints de interfaz
2. Puntos finales de puerta de enlace

- **Elimina** la necesidad de una **puerta de enlace**,
**dispositivo NAT**, **conexión VPN** o
**conexión directa con AWS**
- Las **instancias** en la VPC
**no requieren una dirección IP pública**
para comunicarse con los recursos de servicio
- El **tráfico** entre su VPC y otros servicios
<span class="text-red">**no sale de la red de AWS**</span>

- **Escala horizontal**, **redundante** y **alta disponibilidad**
Componente VPC
- Permite la comunicación segura entre instancias y servicios,
**sin añadir riesgos de disponibilidad ni limitaciones de bandwidth**
en su tráfico

### Puntos finales de interfaz

Los **puntos finales de interfaz** son
<span class="text-red">**Interfaces de red elástica ( ENI )**</span>
con una **dirección IP privada**. Sirven como punto de entrada
para el tráfico que va a un servicio soportado

Los puntos finales de la interfaz son impulsados por **AWS PrivateLink**.
Acceda al servicio alojado en AWS de forma fácil y segura al
manteniendo su tráfico de red dentro de la red de AWS

- Precio por punto final de VPC por AZ $0,01/hora
- Precio por GB de datos procesados $0,01/hora
- ~$7.5/mes

### Puntos finales de gateway

Un **punto final de puerta de enlace** es una puerta de enlace
que es un objetivo **para una ruta específica** en su
**tabla de rutas**, utilizada para el tráfico destinado
a un servicio de AWS compatible

Para crear un Gateway Endpoint, debe especificar la VPC en
que desea crear el endpoint, y el servicio al que
que desea establecer la conexión

Actualmente, AWS Gateway Endpoint sólo admite 2 servicios,
DynamoDB y Amazon S3

*<span class="text-red">**Los puntos finales de la VPC son gratuitos**</span>

## Cheat Sheet

- Los VPC Endpoints ayudan a mantener el tráfico entre los
servicios de AWS **dentro de la red de AWS**
- Hay dos tipos de VPC Endpoints. **Interfaz y puerta de enlace**
- Los puntos finales de interfaz **cuestan dinero**,
los puntos finales de puerta de enlace **son gratuitos**
- Los puntos finales de interfaz utilizan la
interfaz de red elástica ( ENI )
con IP privada ( powered by AWS PrivateLink )
- Gateway Endpoints es un objetivo para una ruta específica en
su tabla de rutas
- Los puntos finales de la interfaz admiten muchos
servicios de AWS
- Los puntos finales de la puerta de enlace
solo admiten DynamoDB y S3

<style>
.text-red {
  color: red;
}
</style>
