# CI/CD

Metodologías automatizadas para **prepare**, **test**, **deliver**
o **deploy** el código en el servidor de producción

## Introducción

### CI/CD Models

- **Producción** - Es el servidor en vivo donde los usuarios
reales de pago utilizan la plataforma
- **Staging** - Es un servidor privado que hace una prueba
manual final como cliente ( QA ) antes de desplegar a producción

### Steps on CI/CD

`Code > Build > Integrate > Test > Release > Deploy`

- **Code hasta Test**
  - Integración continua ( CI )
  - Revisiones automáticas del código del desarrollador
- **Code hasta Release**
  - Entrega continua ( CD )
  - Prepara automáticamente el código del desarrollador para
  su lanzamiento a producción
- **Code hasta Deploy**
  - Despliegue continuo ( CD )
  - Desplegar automáticamente el código tan pronto como el
  desarrollador suba su código y si todas las pruebas pasan

## Continuous Integration

La práctica de automatizar la
**integración de los cambios de código** de múltiples
colaboradores en un solo proyecto de software

Esto fomenta la realización de pequeños cambios con
mayor frecuencia. Cada confirmación desencadena una construcción
durante la cual se ejecutan pruebas que ayudan a identificar
si algo se ha roto con los cambios

Puede utilizar los siguientes servicios de AWS:

- **CodeCommit** - Almacenar en el repositorio
- **Lambda** - Un webhook se dispara y le dice a lambda que
se ejecute
- **CodeBuild** - Crear un nuevo servidor de construcción
- **S3 Bucket** - Reporta el resultado ( informe )

## Continuous Delivery

La práctica de automatizar la preparación del código para
ser liberado a producción o ramas de `staging`.
Usted está preparando el código base para el despliegue.
**El despliegue sigue siendo un proceso manual**.

Puede utilizar los siguientes servicios de AWS:

- **CodeCommit** - Almacenar en el repositorio
- **Lambda** - Un webhook se dispara y le dice a lambda que
se ejecute
- **CodeBuild** - Crear un nuevo servidor de construcción
- **S3 Bucket** - Reporta el resultado ( informe )

## Continuous Deployment

Lo mismo que la Entrega Continua pero **despliega automáticamente**
los cambios a producción

- **CodeCommit** - Almacenar en el repositorio
- **Lambda** - Un webhook se dispara y le dice a lambda que
se ejecute
- **CodeBuild** - Crear un nuevo servidor de construcción
- **S3 Bucket** - Reporta el resultado ( informe )
- **CodeDeploy** - Ver los cambios en la rama maestra y automáticamente
despliega a los servidores de producción

## Cheat Sheet

- CI/CD son metodologías automatizadas que **preparan**, **prueban**,
**entregar** o **desplegar** código en un servidor
- **Producción** un entorno que está destinado a ser utilizado
por usuarios de pago
- **Staging** Un entorno que pretende simular un entorno de
entorno de producción para la última etapa de depuración
- **Integración continua (CI)**
  - Automatizar la revisión del código de los desarrolladores
  - Por ejemplo, ejecutar suites de prueba con un servidor
  de construcción como CodeBuild
- **Entrega continua ( CD )**
  - Automatización de la preparación del código del desarrollador
  para su liberación
  - Por ejemplo, ejecutar suites de prueba con un servidor
  de construcción ( CodeBuild ) y si la prueba pasa, crea
  una solicitud de extracción o fusionar la rama puesta en escena
- **Despliegue continuo ( CD )**
  - Desplegar automáticamente el código del desarrollador
  que está listo para el lanzamiento
  - Por ejemplo, fusionar automáticamente las solicitudes de
  extracción si todas las pruebas pasan y desplegar en producción
  - El despliegue continuo puede referirse a todo el pipeline
  Por ejemplo, CodePipeline usando CodeCommit + CodeBuild + CodeDeploy

<style>
.text-red {
  color: red;
}
</style>
