# Secrets Manager

**Proteger los secretos** necesarios para acceder a sus
aplicaciones y servicios. Rota, gestiona y recupera fácilmente
las credenciales de la base de datos, claves de API y
otros secretos a lo largo de su ciclo de vida

## Introducción

Secrets Manager's se utiliza sobre todo para almacenar y
rotar las credenciales de la base de datos

Hay 5 tipos de secretos disponibles:

- Credenciales para bases de datos RDS
- Credenciales para el cluster Redshift
- Credenciales para bases de datos DocumentDB
- Credenciales para otras bases de datos
- Otros tipos de secretos

**Facilita** el cifrado en reposo mediante el uso de KMS

**CloudTrail** puede supervisar el acceso a las credenciales
en caso de que se necesite auditar

### Precios

- 0.40$ por secreto al mes
- 0.05$ por 10.000 llamadas a la API

<style>
.text-red {
  color: red;
}
</style>
