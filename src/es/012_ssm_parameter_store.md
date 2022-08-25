# SSM Parameter Store

**Seguro**, **almacenamiento jerárquico** para la configuración
de datos y gestión de secretos

## Introducción

Puedes almacenar información como contraseñas, cadenas de
conexión a DB y códigos de licencia como valores

Almacena datos de configuración y cadenas seguras en
**jerarquías** y **seguimiento de versiones**

Puede cifrar los parámetros mediante KMS

Los parámetros se agrupan según la convención de nomenclatura
**utilizando barras diagonales**. Así es como se crean
**jerarquías**. Esto le permite obtener todos los parámetros
en diferentes niveles. Por ejemplo, /exampro/aplicación/prod

Se elige un nivel que limita el número de parámetros y
el tamaño de los valores

El tipo puede ser:

- **String** - Sólo una cadena
- **StringList** - Cadena separada por comas
- **SecureString** - Cadena encriptada con KMS

## Parameter Tiers

|                                       | **Standard** | **Advanced**            |
|---------------------------------------|--------------|-------------------------|
| Número de parámetros                  | 10.000       | 100.000                 |
| Tamaño máximo del valor del parámetro | 4KB          | 8KB                     |
| Políticas de parámetros               | No           | Sí                      |
| Coste                                 | Gratis       | 0,05$ por parámetro/mes |

Puede cambiar el parámetro `standard` a un parámetro `advanced`
en cualquier momento, pero
<span class="text-red">**no se puede revertir un parámetro
`advanced` a uno `standard`**</span>

Revertir un parámetro `advanced` a uno `standard`
**daría lugar a la pérdida de datos** porque el sistema
truncaría el tamaño del parámetro de 8 KB a 4 KB

## Parameter Policies

Las políticas de parámetros son útiles para
**obligar a actualizar o borrar contraseñas**

Usa escaneos asíncronos periódicos. Después de crear una política,
**no es necesario realizar acciones adicionales para hacer cumplir
política**

**Puedes asignar múltiples** políticas a un parámetro

Hay 3 tipos de pólizas:

- **Expiration**
  - Esta <span class="text-red">**política elimina el parámetro**</span>
  después de una fecha y hora especificada
- **ExpirationNotification**
  - Esta política activa un evento en los eventos de Amazon CloudWatch
  que <span class="text-red">**te notifica sobre el
  próximo vencimiento**</span>
- **NoChangeNotification**
  - Esta política activa un evento en Amazon CloudWatch
  <span class="text-red">**si un parámetro no ha sido
  modificado por un período de tiempo específico**</span>.
  Este tipo de política es útil cuando, por ejemplo, una contraseña
  necesita ser cambiada dentro de un período de tiempo

## CLI Hierarchy Examples

```bash
aws ssm put-parameter --name "/planets/vulcan/population"     --value "4.9B" --type String
aws ssm put-parameter --name "/planets/vulcan/gravity"        --value "1.4G" --type String
aws ssm put-parameter --name "/planets/vulcan/classification" --value "M"    --type String
```

```bash
aws ssm get-parameters-by-path --path "/planets/vulcan"
```

<style>
.text-red {
  color: red;
}
</style>
