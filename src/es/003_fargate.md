# Fargate

## Introduction

**Contenedores sin Servidor**. No te preocupes por los servidores.
Ejecuta contenedores y paga en base a la duración y consumo.

- Puedes tener un cluster ECS ( no provisto por
instancias EC2 ) y luego ejecutar `Tasks` como `Fargate`
- Ya no tiene que
<span class="text-red">**aprovisionar**</span>,
<span class="text-red">**configurar**</span>, y
<span class="text-red">**escalar**</span>
clusters de instancias EC2 para ejecutar contenedores
- Se cobra por lo menos un minuto y después por segundo
- Se pagas en base a la duración y el consumo

![ECS vs Fargate](https://i.postimg.cc/65VJ8377/image.png)

## Configurando Fargate Tasks

![Configuring Fargate Tasks](https://i.postimg.cc/kgpVB9hb/image.png)

## Fargate Vs Lambda

Lambda y Fargate son muy similares pero tienen unas
diferencias claves

|                  | **Fargate**                        | **Lambda**                                                |
|------------------|------------------------------------|-----------------------------------------------------------|
| **Cold Starts**  | Si ( menos )                       | Si                                                        |
| **Duración**     | Tanta como quieras                 | 15 min                                                    |
| **Memoria**      | Hasta 30Gb                         | Hasta 3Gb                                                 |
| **Contenedores** | Tú proporcionas los contenedores   | Limitado a contenedores estándar                          |
| **Integración**  | Más Manual                         | Se integra perfectamente con otros servicios sin servidor |
| **Precio**       | Al menos 1 min y luego por segundo | Pagas por 100ms                                           |

<style>
.text-red {
  color: red;
}
</style>
