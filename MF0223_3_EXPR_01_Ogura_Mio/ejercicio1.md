# EJERCICIO 1 — Despliegue de entorno Linux con Docker Compose

La empresa TechCore necesita desplegar un entorno Linux básico para realizar tareas internas.
Se ha proporcionado un archivo de configuración **docker-compose.yml*, el cual presenta posibles errores y/o configuraciones inadecuadas.
Tu tarea consiste en analizar dicho archivo, identificar los problemas existentes, corregirlos para obtener una configuración coherente y funcional, y justificar técnicamente cada una de las decisiones tomadas.

ejecutar:
```
docker compose up -d
```

Sin corregir nada, salió estos errores:

```
time="2026-05-27T17:46:30+02:00" level=warning msg="C:\\Users\\gusw0\\Desktop\\IFCD0112_02\\test\\MF0223_3_EP_Ogura_Mio\\MF0223_3_EXPR_01_Ogura_Mio\\docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion"
service "srv_dev_XX" refers to undefined network net_devXX: invalid compose project

```

- nombre de networks son diferentes
  net_devXX, net_dev_XX
- eliminar version porque no necesario 

ERROR MESSAGE:
```
unable to get image 'ubuntu:22': error during connect: Get "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/v1.51/images/ubuntu:22/json": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.
```

- imagen ubuntu:22 no existe, uso ubuntu:22.04

