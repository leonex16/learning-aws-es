# CloudFront

Red de distribución de contenidos ( CDN )
Crea copias en caché de su sitio web en
varias `Edge Locations` en todo el mundo

## Introduction

### Content Delivery Network ( CDN )

Una CDN es una red distribuida de servidores que entrega
páginas web y contenidos a los usuarios en función de su
**ubicación geográfica**, el **origen de la página web**,
y una **entrega de contenido**

Puede utilizarse para **entregar una página web completa**,
incluyendo información estática, dinámica y de streaming

Las solicitudes de contenido se sirven desde la `Edge Locations
más cercana para obtener el mejor rendimiento posible

## Core Components

### Origin

La ubicación donde se encuentran todos los archivos originales.
Por ejemplo, un S3 Bucket, una instancia EC2, un ELB o un Route53

### Edge Location

La ubicación en la que se almacenará en caché el contenido web.
Esto es diferente que una región de AWS o AZ

### Distribution

Una colección de `Edge Locations` que define
cómo debe comportarse el contenido en caché

## Distributions

Una distribución es una colección de Edge Locations.
Usted especifica el origen, por ejemplo, S3, EC2, ELB o Route53

Replica copias basadas en su **Categoría de precios**.

Hay 2 tipos de distribuciones

1. Web ( para sitios web )
2. RTMP ( para streaming de medios )

### Behaviors

Redirigir a HTTPs, Restringir métodos HTTP,
Restringir el acceso del espectador, Establecer TTLs

### Invalidations

Puede invalidar manualmente la caché de determinados archivos
mediante invalidaciones

### Error Pages

Puede servir páginas de error personalizadas, por ejemplo 404

### Restrictions

Puede utilizar **Restricción geográfica** para poner en
lista negra o lista blanca de países específicos

## Lambda Edge

Utilizamos las funciones de Lambda@Edge para
**sobrescribir el comportamiento** de **solicitud y respuesta**.

Las 4 funciones Lambda@Edge disponibles

1. **Solicitud del espectador** - Cuando CloudFront recibe
una solicitud de un espectador
2. **Solicitud de origen** - Antes de que CloudFront reenvíe
una solicitud al origen
3. **Respuesta de origen** - Cuando CloudFront recibe una respuesta
del origen
4. **Respuesta del espectador** - Antes de que CloudFront
devuelva la respuesta al espectador

<img
  src="../../public/images/cloudfront/lambda_edge_fn.png"
  alt="Funciones Lambda@Edge" />

## Protection

Por defecto una distribución **permite que todos tengan acceso**

**Identidad de acceso de origen ( OAI )** - Una identidad de
usuario virtual que se utilizará para dar a su distribución
de CloudFront permiso para obtener un objeto privado

Para utilizar URLs firmadas o Cookies firmadas necesita
tener una **OAI**

**URLs firmadas**
( No es lo mismo que la URL pre-firmada de S3 )

Una url con proporciona acceso temporal a objetos en caché

**Cookies firmadas.**

Una cookie que se pasa junto con la solicitud a CloudFront.
La ventaja de utilizar una cookie es que se quiere proporcionar
acceso a múltiples archivos restringidos. Por ejemplo, la transmisión
de vídeo

## Cheat Sheet

- CloudFront es una CDN ( Red de Distribución de Contenidos ).
Hace que sitio web cargue rápidamente sirviendo
contenido en caché
- CloudFront distribuye la copia en caché en **Edge Locations**.
- Las ubicaciones de borde no son sólo de lectura,
se puede escribir en ellas, por ejemplo, objetos PUT
- **TTL** ( Time to live ) define el tiempo que falta para
que la caché caduque
- Cuando se invalida la caché, se está forzando a que
expire inmediatamente ( refresca los datos de la caché )
- Refrescar la caché **cuesta dinero debido a los costes de transferencia**
para actualizar las `Edge Locations`
- **Origen** es la dirección de donde residen las copias de
origen de sus archivos residen, por
ejemplo, S3, EC2, ELB, o Route53
- **Distribución** define una colección de Edge Locations y
comportamiento sobre cómo debe manejar su contenido en caché
- Las **Distribuciones** tienen 2 tipos:
  - **Distribución web** - Contenido estático de sitios web
  - **RTMP** - Medios de comunicación en streaming
- **Origin Access Identity ( OAI )** se utiliza el acceso privado
a Buckets S3
- El acceso al contenido en caché puede ser protegido
a través de **Las URLs firmadas** o **Las cookies firmadas**
- **Lambda@Edge** permite pasar cada petición a través de una
Lambda para cambiar el comportamiento de la respuesta

<style>
.text-red {
  color: red;
}
</style>
