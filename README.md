**Sistema Seguro de Transacciones Financieras**

Breve recopilación de scripts y utilidades para experimentar con mecanismos de seguridad en transacciones financieras simuladas (cliente/servidor, DB, pruebas de ataque como MITM y replay). Este repositorio contiene código de ejemplo destinado a investigación y pruebas en entornos controlados.

**Resumen**
- **Propósito:** Proveer herramientas para simular, analizar y probar protocolos/implementaciones de transacciones seguras (cliente, servidor, cifrado, DB y ataques controlados).
- **Ámbito:** Código de apoyo para pruebas locales y educativas. No usar en entornos de producción sin auditoría y adaptación.

**Requisitos**
- **Python:** `3.8+`.
- **Paquetes recomendados:** `psycopg2-binary` (si usa PostgreSQL), `cryptography` o librerías de cifrado que el proyecto utilice. Instalar con `pip` según sea necesario.

**Instalación rápida**
- Crear un entorno virtual (opcional):
  ```powershell
  python -m venv .venv; .\.venv\Scripts\Activate.ps1
  ```
- Instalar dependencias (si crea `requirements.txt`):
  ```powershell
  pip install -r requirements.txt
  ```
- Si no hay `requirements.txt`, instalar los paquetes que necesite, por ejemplo:
  ```powershell
  pip install psycopg2-binary cryptography
  ```

**Uso básico**
- Iniciar el servidor (escuchar transacciones):
  ```powershell
  python python\serversocket.py
  ```
- Ejecutar el cliente que envía transacciones:
  ```powershell
  python python\clientsocket.py
  ```
- Scripts de prueba / ataque (usar sólo en entornos de laboratorio):
  ```powershell
  python python\clientsocket_atack.py    # cliente malicioso de prueba
  python python\mitm.py                 # man-in-the-middle de prueba
  python python\replay.py               # ensayo de replay attacks
  ```

**Configuración de base de datos**
- Los comandos y ejemplos relacionados con PostgreSQL se encuentran en `comandos_postgres.txt` y en `python/postgresql_functions.py`.
- Cree la base de datos y tablas necesarias siguiendo `comandos_postgres.txt` o adaptando las funciones del archivo `postgresql_functions.py`.

**Estructura del proyecto**
```
clientesocket_transaccion.txt
comandos_postgres.txt
README.md
python/
    clientsocket.py
    clientsocket_atack.py
    db_crypt.py
    descifrar.py
    mitm.py
    nonce_functions.py
    postgresql_functions.py
    replay.py
    serversocket.py
    time_functions.py
```

**Descripción de archivos principales**
- `python/clientsocket.py`: Cliente que simula envío de transacciones al servidor.
- `python/clientsocket_atack.py`: Cliente malicioso para pruebas (simula ataques).
- `python/serversocket.py`: Servidor que recibe y procesa transacciones.
- `python/mitm.py`: Script para pruebas de man-in-the-middle (intercepción y manipulación) en entornos controlados.
- `python/replay.py`: Utilidad para reproducir mensajes y probar mecanismos anti-replay.
- `python/db_crypt.py`: Funciones relacionadas con cifrado/descifrado y almacenamiento seguro.
- `python/descifrar.py`: Herramienta/ejemplo para descifrar mensajes según el formato usado en el repo.
- `python/nonce_functions.py`: Generación y validación de nonces para protección contra reenvíos.
- `python/postgresql_functions.py`: Conectores y funciones para interactuar con PostgreSQL.
- `python/time_functions.py`: Funciones de tiempo/espera usadas por los scripts.
- `clientesocket_transaccion.txt`: Ejemplos de transacciones que puede enviar el cliente.
- `comandos_postgres.txt`: Comandos de ejemplo para crear DB/tablas y usuarios en PostgreSQL.

**Buenas prácticas y advertencias**
- Use este código sólo en entornos de laboratorio o desarrollo. No emplee scripts de ataque (`clientsocket_atack.py`, `mitm.py`, `replay.py`) contra sistemas reales sin autorización.
- Verifique y ajuste configuraciones de red y base de datos antes de ejecutar.

**Cómo contribuir**
- Haga forks y pull requests para mejorar documentación, añadir `requirements.txt` o facilitar la configuración.
- Abra issues para reportar errores o proponer mejoras.

**Licencia**
- (Pendiente) Añada una licencia apropiada en el repositorio cuando decida la política de uso.

**Contacto**
- Autor/Contacto: `Josesolis01` (repositorio: `Sistema-Seguro-Transacciones-Financieras`).

Si quieres, puedo:
- generar un `requirements.txt` sugerido según importaciones reales en `python/`,
- añadir ejemplos más detallados de configuración de PostgreSQL,
- o traducir y/o mejorar secciones concretas del README.
