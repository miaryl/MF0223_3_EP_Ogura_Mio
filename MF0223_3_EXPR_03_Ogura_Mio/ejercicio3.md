# EJERCICIO 3 — Diagnóstico y recuperación de rendimiento en sistema Linux

## Contexto

Tras ejecutar un script de mantenimiento en el servidor de la empresa, se ha detectado un comportamiento anómalo en el sistema.
Se sospecha que el script ejecutado ha provocado estos problemas.

Tu misión es actuar como técnico de sistemas y:

● analizar el estado del sistema

● detectar el origen del problema

● aplicar las medidas necesarias para solucionarlo

## OBJETIVOS

● Monitorizar el sistema Linux

● Analizar procesos en ejecución

● Evaluar uso de CPU, memoria y disco

● Detectar procesos anómalos

● Liberar recursos del sistema

● Restaurar el funcionamiento normal

## SCRIPT EJECUTADO (INFORMATIVO)

El siguiente script ha sido ejecutado previamente:

```
#!/bin/bash
yes > /dev/null &
yes > /dev/null &
yes > /dev/null &
cat /dev/zero | head -c 300M > /tmp/mem_test1 &
cat /dev/zero | head -c 300M > /tmp/mem_test2 &
mkdir -p /tmp/test_disk
for i in {1..30}
do
dd if=/dev/zero of=/tmp/test_disk/file_$i bs=1M count=5
done

```

## TAREAS

### 1. Análisis de CPU

● procesos que consumen CPU

● qué comando has utilizado

```bash
ps aux --sort=-%cpu | head -10
top
```

- se detectan procesos yes ejecutandose en segundo plano. Estos procesos consumen casi el 100% de la CPU y no realizan ninguna tarea útil.

### 2. Análisis de procesos

● Listar los procesos activos

● Identificar procesos sospechos

```bash
ps aux
ps aux | egrep "yes|dd|cat"
```

- Se identifican procesos sospechosos:

yes (alto consumo de CPU)

cat /dev/zero (uso de memoria)

dd (escritura de archivos en disco)

### 3. Análisis de memoria

● Comprobar el uso de memoria del sistema

`free -h`

### 4. Análisis de disco

● Identificar qué directorios ocupan más espacio

● Comprobar el estado general del disco

`df -h`

### 5. Diagnóstico

Responder:

● ¿Qué está causando el problema?

● ¿Qué tipo de procesos están afectando al sistema?

- el sistema está lento porque se ejecutó un script que:
crea procesos yes -> sobrecarga CPU
usa cat /dev/zero -> consume memoria
usa dd en bucle -> llena el disco

En general, son procesos de estrés que saturan el sistema

### 6. Solución

Debes:

● detener los procesos problemáticos

● liberar memoria

● eliminar archivos innecesarios

```bash
pkill yes
pkill cat
pkill dd
```

- eliminar los procesos que causan la sobrecarga.


### 7. Verificación

● Comprobar que el sistema vuelve a la normalidad

```bash
top
free -h
df -h
ps aux | egrep "yes|dd|cat"
```

- Resultado

El sistema vuelve a la normalidad:

CPU estable

memoria libre

disco limpio

no hay procesos sospechosos
