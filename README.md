# Portal Financiero (Homebanking & Admin) — Banco de la Nación (Perú)

Este es el frontend del sistema de simulación financiera del **Banco de la Nación (Perú)**. Es una SPA (Single Page Application) rica e interactiva construida sobre **React** y **Vite**, que simula tanto la **Banca por Internet (Homebanking)** para los clientes como la consola de **Administración, Control de Riesgos y Cobranzas** del banco.

---

## 🛠️ Stack Tecnológico del Frontend

*   **Librería Principal:** React 18.
*   **Herramienta de Construcción:** Vite (Carga ultra-rápida y desarrollo optimizado).
*   **Iconografía:** Lucide React.
*   **Estilos:** Vanilla CSS moderno con variables de diseño customizadas (Aesthetics Premium con colores del Banco de la Nación).
*   **Cliente HTTP:** Fetch API / Axios para consumir la REST API del backend.

---

## 💻 Módulos y Vistas Implementadas

El portal se divide en dos grandes universos según el perfil del usuario:

### 1. Banca por Internet (Portal de Clientes)
*   **Login Seguro:** Autenticación robusta conectada al backend de FastAPI. Guarda el token JWT en el almacenamiento del navegador de forma segura.
*   **Posición Consolidada:** Resumen ejecutivo de las cuentas de ahorro del usuario (soles y dólares) y saldos contables/disponibles.
*   **Simulador de Crédito Multired:** Permite al cliente estimar sus cuotas mensuales ingresando el monto y plazo, y elegir si incluye o no seguro de desgravamen (aplicando el tarifario oficial del Banco de la Nación).
*   **Bandeja de Movimientos:** Historial detallado de todas las transacciones de las cuentas del cliente.
*   **Operaciones Financieras:**
    *   Transferencias directas e interbancarias diferidas/inmediatas (CCE).
    *   Pago de servicios públicos.
    *   Pago de cuotas pendientes del crédito Multired directamente de los fondos del cliente.

### 2. Consola de Administración (Portal del Empleado Bancario)
*   **Dashboard de Control:** Resumen global de clientes, cuentas activas, total desembolsado y estadísticas financieras generales.
*   **Maker-Checker (Aprobación por Rangos de Monto):** 
    *   Los empleados de la agencia pueden ver las solicitudes registradas.
    *   Las firmas y aprobaciones se habilitan visualmente y por lógica de API según el rol y monto (Asesor, Gerente Regional o Comité de Riesgos).
*   **Módulo de Cobranzas y Mora (Recuperaciones):**
    *   Visualización de créditos vencidos por bandas de mora (*Preventivo*, *Temprano*, *Tardío*, *Judicial*, *Castigo*).
    *   Registro interactivo de compromisos de pago del cliente moroso y control de transiciones de estados del crédito.
*   **Integración con Power BI:**
    *   Consola interactiva que guía al administrador para conectar **Power BI Desktop** mediante endpoints JSON.
    *   Botones de copiado rápido de URLs y guías de modelado estrella y configuración de cabeceras HTTP.

---

## 🎨 Diseño y Personalización Visual
La interfaz ha sido adaptada con una **identidad premium** basada en la imagen corporativa del **Banco de la Nación**:
*   Paleta de colores institucionales: Rojos corporativos, grises limpios y contrastes oscuros elegantes.
*   Tipografía limpia y moderna.
*   Diseño responsive adaptado a múltiples dispositivos (móvil, tablet y escritorio).
*   Micro-animaciones fluidas en botones, alertas y transiciones de formularios.

---

## 🚀 Despliegue en Producción (Vercel)

El frontend está optimizado para compilarse como un conjunto de archivos estáticos HTML/JS y servirse desde la red de borde de **Vercel**:

1. Crea una cuenta o inicia sesión en **Vercel** y añade un nuevo proyecto enlazado a tu Git.
2. Configura los siguientes parámetros en el asistente de Vercel:
   *   **Root Directory (Carpeta Raíz):** Selecciona `BancoNacion_Frontend`.
   *   **Framework Preset:** Elige **Vite**.
3. En la sección **Environment Variables (Variables de Entorno)**, añade la URL pública de tu API del backend (desplegado en Coolify):
   *   **Nombre:** `VITE_BASE_URL`
   *   **Valor:** `https://api-banco-nacion.coolify.io` *(URL de tu backend sin barra diagonal al final)*
4. Presiona **Deploy**. Vercel compilará automáticamente usando `npm run build` y generará la URL de producción.

---

## 💻 Configuración para Desarrollo Local

1. Navega a la carpeta del proyecto e instala las dependencias de Node.js:
   ```bash
   cd BancoNacion_Frontend
   npm install
   ```
2. Crea un archivo `.env` en la raíz de esta carpeta con la URL de tu API local:
   ```env
   VITE_BASE_URL=http://localhost:8002
   ```
3. Inicia el servidor de desarrollo local:
   ```bash
   npm run dev
   ```
4. Abre [http://localhost:5173](http://localhost:5173) en tu navegador para ver la aplicación ejecutándose.
