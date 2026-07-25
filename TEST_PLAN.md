# 📋 Plan de Pruebas de Software (Test Plan)
**Proyecto:** E-Commerce Platform  
**Módulo:** Autenticación, Catálogo y Carrito de Compras  
**Autor:** QA Engineer  
**Fecha:** Julio 2026  

---

## 1. 🎯 Objetivo del Documento
Definir la estrategia, alcance, recursos y cronograma para la ejecución de pruebas funcionales y no funcionales del sistema E-Commerce, garantizando que las funcionalidades críticas operen sin errores antes de su liberación a producción.

---

## 2. 📌 Alcance (Scope)

### 2.1. Dentro del Alcance (In-Scope)
* **Módulo de Usuarios:** Registro de nuevo usuario, Login (exitoso/fallido), Cierre de sesión.
* **Módulo de Catálogo:** Visualización de productos, filtrado por categorías, búsqueda de productos.
* **Módulo de Carrito:** Agregar producto, modificar cantidades, eliminar producto, cálculo de total.
* **Pruebas de Usabilidad y UI:** Validación de mensajes de error, botones, campos obligatorios y diseño responsivo.

### 2.2. Fuera del Alcance (Out-of-Scope)
* Pasarela de pagos real (Stripe/PayPal en entorno de producción).
* Pruebas de carga y rendimiento masivo (se abordarán en otra fase).
* Pruebas de seguridad e inyección SQL avanzadas.

---

## 3. 🛡️ Matriz de Gestión de Riesgos

| ID | Riesgo Identificado | Impacto | Mitigación |
| :--- | :--- | :--- | :--- |
| **R-01** | La API mock de FakeStore o el backend puede presentar lentitud/caídas durante la prueba. | **Alto** | Utilizar respuestas mockeadas locales o un entorno alternativo para la ejecución UI. |
| **R-02** | Tiempos de respuesta lentos en el carrito de compras afectando la experiencia de usuario. | **Medio** | Validar timeouts y mensajes de espera apropiados en el frontend. |
| **R-03** | Incompatibilidad de diseño en diferentes resoluciones de pantalla. | **Bajo** | Ejecutar pruebas cruzadas de UI en vista Desktop y Mobile. |

---

## 4. ⚙️ Criterios de Aceptación y Salida

* **Criterio de Entrada (Entry Criteria):**
  * Entorno de QA desplegado y estable.
  * Historias de usuario y requerimientos aprobados.
  * Casos de prueba diseñados y revisados.

* **Criterio de Salida (Exit Criteria):**
  * 100% de los casos de prueba ejecutados.
  * 0 defectos abiertos de severidad **Bloqueante (Blocker)** o **Crítica (Critical)**.
  * Todos los defectos menores documentados con su reporte correspondiente.

---

## 5. 💻 Entorno de Pruebas (Test Environment)
* **Navegadores:** Google Chrome (Última versión), Mozilla Firefox.
* **Dispositivos:** Desktop (1920x1080) y Mobile Viewport (iPhone 15 Pro / Galaxy S21).
* **Herramientas de Gestión:** Markdown, GitHub, DevTools de Chrome.