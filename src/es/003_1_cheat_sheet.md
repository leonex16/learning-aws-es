# ECS and Fargate Cheat Sheet

- Servicio de administración de **contenedores**
Altamente seguro, fiable y es una forma
escalable de ejecutar contenedores
- **Componentes de ECS**
  - **Cluster:** Múltiples instancias EC2 que estarán
  en un contenedor docker
  - **Task Definition:** Archive JSON que define la
  configuración de ( hasta 10 ) contenedores que quieras ejecutar
  - **Task:** Ejecuta contenedores definidos en `Task Definition`.
  Las tareas no permanecen en ejecución una vez que se
  ha completado la cargo de trabajo
  - **Service:** Se asegura que las tareas permanezcan ejecutándose
  eg. web-apps servers
  - **Container Agent:** Binario en cada instancia EC2
  que supervisa, inicia y detiene tareas
- **Elastic Container Registry ( ECR )** Servicio totalmente
  gestionado que hace fácil **guardar**,
  **administrar** y **desplegar** imágenes Docker
- **Fargate** son **Contenedores sin Servidor**.
  No te preocupes por los servidores. Ejecuta contenedores y
  paga en base a la duración y consumo.
  - Fargate tiene **Cold Starts** por lo que si es un problema
  puedes usar ECS
  - **Duración:** Tanta como quieras
  - **Memoria:** Hasta 30Gb
  - **Contenedores:** Tú proporcionas los contenedores
  - **Integración:** Más Manual
  - **Precio:** Al menos 1 min y luego por segundo
