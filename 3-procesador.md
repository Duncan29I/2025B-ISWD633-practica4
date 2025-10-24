# Limitar uso de procesador
Limitar la cantidad de núcleos de CPU:
```
--cpus=<número de núcleos>
```

Asignar núcleos de CPU específicos:
```
--cpuset-cpus=<lista de núcleos>
```

**¿Como saber el numero de procesadores virtuales que tiene una máquina?**
Método 1: Con el Administrador de tareas

1. Presiona Ctrl + Shift + Esc para abrir el Administrador de tareas.

2. Ve a la pestaña Rendimiento → CPU.

3. En la parte inferior derecha verás:

Núcleos (Cores)

Procesadores lógicos (Logical processors) → 🔹 Este número son los procesadores virtuales (vCPUs).

## Ejemplo: Si ves “4 núcleos y 8 procesadores lógicos”, tu máquina tiene 8 procesadores virtuales.

Método 2: Con línea de comandos (CMD o PowerShell)

Abre PowerShell o CMD y escribe:

wmic cpu get NumberOfCores,NumberOfLogicalProcessors

## Ejemplos
_Puedes copiar y ejecutar directamente cada uno de los comandos_

Limitar el uso de CPU a 1.5 núcleos
```
docker run -d --name server-nginx --cpus="1.5" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 0 a 2:
```
docker run -d --name server-nginx --cpuset-cpus="0-2" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 1 y 3:
```
docker run -d --name server-nginx --cpuset-cpus="1,3" nginx:alpine
```
