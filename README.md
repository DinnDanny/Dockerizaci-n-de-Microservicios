# Dockerización de Microservicios
**Estudiante:** Angela Arcos
**Institución:** Instituto Superior Tecnológico Universitario Japón

---

## 1. Introducción
Docker es una plataforma de código abierto que permite a los desarrolladores empaquetar, distribuir y ejecutar aplicaciones dentro de contenedores. Un contenedor es una unidad estándar de software que empaqueta el código y todas sus dependencias para que la aplicación se ejecute de forma rápida y confiable de un entorno informático a otro. Sirve para eliminar el clásico problema de "en mi máquina sí funciona", garantizando la paridad entre desarrollo y producción.

## 2. Microservicios dockerizados
En este proyecto se han implementado y configurado los siguientes servicios:
* **Microservicio de Clientes:** Desarrollado en **.NET 8**.
* **Microservicio de Pedidos:** Desarrollado en **Python** (ubicado en la carpeta `apiPy`).
* **Servicio de Mensajería:** Utilizando **RabbitMQ**.
* **Base de Datos:** Utilizando **PostgreSQL** (Imagen `postgres:alpine3.14`).

## 3. Dockerfile por servicio
Cada servicio cuenta con su propio archivo `Dockerfile` para definir su entorno:

* **Dockerfile (.NET):** Utiliza un sistema de compilación multi-etapa (Multi-stage build) con el SDK 10.0 para compilar y el ASP.NET 10.0 para ejecutar, optimizando el tamaño de la imagen final.
* **Dockerfile (Python):** Configura un entorno ligero basado en `python:3.11-slim`, instala las dependencias desde `requirements.txt` y expone el servicio.

---
### 📸 Evidencia de Configuración
> **Imagen a colocar aquí:** `dockerfile_net_core.png` (La captura de tu código en Visual Studio).
---

## 4. Ejecución de contenedores
Para poner en marcha el ecosistema de microservicios, se utilizaron los siguientes comandos en la terminal:

1.  **Construcción de imagen individual:** `docker build -t api-cliente .`
2.  **Levantamiento orquestado:** `docker-compose up -d`
3.  **Verificación de logs:** `docker logs api-cliente-contenedor`

## 5. Configuración
Se establecieron las siguientes conexiones y puertos:
* **API .NET:** Puerto `8080`.
* **PostgreSQL:** Puerto local `5434` mapeado al `5432` del contenedor.
* **RabbitMQ:** Puertos `5672` (datos) y `15672` (panel de administración).
* **Red:** Los contenedores se comunican entre sí mediante la red interna de Docker.

## 6. Evidencias de Funcionamiento

### A. Proceso de Build Orquestado
Esta captura muestra la creación de las capas de imagen mediante Docker Compose.
> **Imagen a colocar aquí:** `build_orquestado_compose.png`

### B. Contenedores en Ejecución (docker ps)
Validación de que todos los servicios (API, DB, RabbitMQ) están en estado "Up".
> **Imagen a colocar aquí:** `servicios_activos_final.png` o `image_636f45.png`

### C. Logs de la Aplicación
Prueba de que la API interna ha iniciado correctamente y está escuchando peticiones.
> **Imagen a colocar aquí:** `logs_ejecucion_docker.png` o `image_6372c9.png`

---

## 7. Conclusión
La implementación de este proyecto permitió comprender la importancia de la arquitectura de microservicios y su despliegue mediante contenedores. Se logró estandarizar el entorno de ejecución, simplificar la gestión de bases de datos y servicios de mensajería, y automatizar el despliegue con Docker Compose, lo cual es fundamental para el desarrollo de aplicaciones distribuidas modernas y escalables.
