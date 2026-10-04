# Levantamiento del Proyecto Asignado

  

**Instituto Politécnico Nacional**  

**Escuela Superior de Cómputo (ESCOM)**  

**Asignatura:** Bases de Datos  

**Práctica 2:** "Modelo Entidad-Relación Extendido: proyecto propio y proyecto asignado"  

**Ejercicio 2:** Clonar y poner en funcionamiento el proyecto asignado  

  

**Profesor:** Hurtado Avilés Gabriel  

**Equipo:**

* Espinosa Ramírez José Luis

* Rojas Castro Alejandro Tonatiuh

* Zamudio Monroy Gael Armando

  

**Grupo:** 3BV1  

**Fecha de Entrega:** 8 de octubre de 2026

  

---

  

## 1. Requisitos

  

Para poner este proyecto en funcionamiento se requiere del siguiente software y herramientas:

* **Docker Desktop**

* **WSL 2** (Windows Subsystem for Linux 2)

* **Git**

* **Cuenta de GitHub**

  

---

  

## 2. Hacer un Fork y Clonar el Repositorio

  

1. **Fork del Repositorio:**

   * Se realizó el fork del repositorio original `Seismic-Data-Visualization-System` directamente desde la interfaz web de GitHub (`github.com`) hacia la cuenta (`GaelZamudio/Seismic-Data-Visualization-System`).

  

2. **Clonación del Fork:**

   * Desde la terminal de comandos (CMD) en la máquina local, se ejecutó el comando para clonar el repositorio forkeado:

   ```bash

   git clone https://github.com/GaelZamudio/Seismic-Data-Visualization-System.git

   ```

  

---

  

## 3. Ejecución del Proyecto

  

1. **Iniciar el entorno:**

   * Se abrió la aplicación **Docker Desktop** para asegurar que el motor de contenedores estuviera en ejecución.

  

2. **Levantar los servicios:**

   * Dentro del directorio del proyecto clonado (`Seismic-Data-Visualization-System`), se ejecutó el siguiente comando en la terminal para construir y levantar los contenedores en segundo plano:

   ```bash

   docker compose up -d

   ```

   *(ver captura de terminal durante el arranque: `evidencias/terminal-arranque.png`)*

  

   * **Proceso observado:** Docker descargó la imagen base de PostgreSQL (`postgres:17`) y construyó la imagen del servidor web PHP/Apache (`seismic-data-visualization-system-web`), creando la red `app-network`, el volumen de datos de la base de datos y levantando los contenedores `seismic-data-visualization-system-db-1` y `seismic-data-visualization-system-web-1`.

  

---

  

## 4. Errores Encontrados y Solución

  

* **Descripción del Error:**

  * Al acceder a la aplicación en el navegador web local (`http://localhost/vista.html`), la página presentó una falla de conexión inicial con el servidor PostgreSQL:

  > `Warning: pg_connect(): Unable to connect to PostgreSQL server: connection to server at "db" (172.18.0.2), port 5432 failed: Connection refused...`  

  > **Error en el Sistema:** *Failed to connect to database: Connection refused*

  *(ver captura del error: `evidencias/ejecucion-error.png`)*
  

* **Causa y Solución:**

  * El contenedor de la base de datos aún no terminaba de inicializar completamente sus scripts cuando el contenedor web intentó realizar las primeras peticiones.

  * Se procedió a reiniciar los servicios ejecutando:

    ```bash

    docker compose down

    docker compose up -d

    ```

  * Tras reiniciar los contenedores, la aplicación funcionó correctamente, desplegando el **Sistema de Visualización de Datos Sísmicos (MUTVI 2025, UAM Azcapotzalco)** y cargando la información de los sismos en el mapa interactivo.  

  *(ver captura de la aplicación funcionando: `evidencias/app-funcionando.png`)*

  

---

  

## 5. Consulta Directa a la Base de Datos

  

Se realizó una consulta directamente sobre la base de datos PostgreSQL del proyecto utilizando un cliente SQL (pgAdmin).

  

* **Consulta SQL Ejecutada:**

  ```sql

  SELECT * FROM dim_zonas;

  ```

  

* **Resultado Obtenido:**

  * La consulta retornó exitosamente los registros de la tabla `dim_zonas`, mostrando columnas como `id_zonas`, `entidad`, `nom_ent`, entre otros datos.  

  *(ver captura de la consulta con su resultado: `evidencias/consulta-resultado.png`)*