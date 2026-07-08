# 📊 Seguimiento de Grupos de Trabajo — Coordinación Activa en Tiempo Real

¡Bienvenido/a! Esta es una aplicación web monocapa (Single Page Application) modular, moderna y responsiva diseñada para facilitar la tutorización, mentoría y coordinación de dinámicas de trabajo en equipo o talleres educativos en tiempo real. 

Permite a los usuarios (alumnos/equipos) reportar bloqueos, hitos de finalización y autoevaluaciones pedagógicas, mientras que ofrece una consola centralizada para el ponente o administrador.

---

## 🚀 Características Principales

La aplicación se divide en dos entornos principales conmutables mediante un selector de roles superior:

### 👤 Vista de Usuario (Equipos de Trabajo)
* **Datos del Equipo:** Selección interactiva del número de grupo. El reto en curso se bloquea de forma remota según las directrices del ponente.
* **🚨 Comunicación de Incidencias:** Envío inmediato de alertas de asistencia clasificadas por 5 niveles de urgencia (utilizando un sistema interactivo de estrellas) y una descripción en texto del bloqueo.
* **🏁 Hito "¡Reto Completado!":** Botón de acción rápida con advertencia integrada para avisar al ponente de forma visual en cuanto todo el equipo termine.
* **🎓 Valoración del Aprendizaje:** Formulario de reflexión pedagógica final que evalúa mediante métricas de estrellas la *Dificultad*, el *Logro alcanzado* y la *Aplicabilidad*, junto a campos abiertos para aprendizajes adquiridos y dudas pendientes.

### ⚙️ Vista de Administrador (Panel del Ponente)
* **Sincronización Remota de Retos:** Cambiar el reto activo actualiza instantáneamente las pantallas de todos los usuarios conectados sin refrescar la página.
* **📦 Cuadro de Mandos en Vivo:** Widget dinámico lateral que cuenta y lista en tiempo real los grupos que completan el reto activo.
* **🛑 Panel de Incidencias Exclusivo:** Tabla de recepción ordenada de forma descendente por retos, destacando visualmente los niveles de urgencia.
* **📝 Panel de Valoraciones:** Espacio limpio y estructurado para leer el progreso de los equipos y detectar dudas pedagógicas recurrentes.
* **📥 Exportación Avanzada:** Descarga de datos acumulados localmente en formatos estructurados **Excel (CSV)** y **Markdown** listos para informes académicos.

---

## 🛠️ Stack Tecnológico y Arquitectura

* **Frontend:** HTML5, CSS3 Nativo (con variables configurables `:root`) y JavaScript Moderno (ES6+).
* **Iconografía y Tipografía:** [FontAwesome 6.4.0](https://fontawesome.com/) e [Inter Font](https://fonts.google.com/specimen/Inter) para una visualización premium y legible.
* **Sincronización Local Inter-Pestañas:** Implementación de la API nativa de JavaScript `BroadcastChannel`, lo que permite simular un entorno de red local y transmitir datos en tiempo real entre múltiples pestañas del navegador sin requerir un servidor intermedio.
* **Persistencia:** Respaldo local de configuraciones e historial de envíos mediante `localStorage`.
* **Persistencia Cloud Real (Opcional):** Integración nativa preparada mediante método HTTP `POST` hacia webhooks de **Google Apps Script** para volcar las respuestas automáticamente en hojas de cálculo de **Google Sheets**.

---

## ⚙️ Configuración e Integración con Google Sheets

Para activar el almacenamiento persistente en la nube a través de Google Drive, sigue estos pasos:

1. Crea una hoja de cálculo en **Google Sheets** con las columnas necesarias para almacenar los registros de tus retos (Grupo, Reto, Tipo, Métricas, Comentarios...).
2. Extiende un script en **Extensions > Apps Script** que reciba las peticiones por el método `doPost(e)` e inserte los datos en formato JSON.
3. Publica el script como **Aplicación Web** y configura el acceso para *"Cualquiera, incluso anónimo"*.
4. Copia la URL de ejecución generada (`https://script.google.com/macros/s/.../exec`).
5. Accede a la **Vista Administrador** de esta aplicación, pégala en el input **Apps Script Web App URL** y define el número máximo de grupos concurrentes de tu sesión.

---

## 📁 Estructura del Archivo

El proyecto está autocontenido en un único archivo de producción de alto rendimiento:

```text
└── index.html        # Contiene toda la estructura semántica, los estilos de diseño y la lógica reactiva.
