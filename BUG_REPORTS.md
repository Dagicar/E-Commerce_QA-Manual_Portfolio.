# 🐞 Registro y Reporte de Defectos (Bug Reports)
**Proyecto:** E-Commerce Platform  
**Documento Relacionado:** [Matriz de Casos de Prueba](TEST_CASES.md)  

---

## 📌 Reporte de Defectos Registrados

### 🐛 BUG-01: El buscador del catálogo muestra pantalla en blanco al no encontrar resultados

* **ID del Defecto:** `BUG-01`
* **Caso de Prueba Relacionado:** `TC-CAT-02`
* **Severidad:** **Media (Medium)** — Afecta la experiencia de usuario pero no bloquea el sistema.
* **Prioridad:** **Alta (High)** — Debe corregirse en el sprint actual para evitar confusión visual.
* **Módulo / Componente:** Frontend UI - Filtro de Búsqueda
* **Estado:** **Open (Abierto)**
* **Entorno:** Google Chrome v126.0 (Windows 11) / Mobile Viewport (iPhone 15 Pro)

---

#### 📝 Descripción
Al ingresar un término de búsqueda que no coincide con ningún producto existente en la base de datos (por ejemplo, `xyz123999`), la aplicación no muestra ningún mensaje informativo de "Sin resultados" y deja la grilla de productos en blanco sin retroalimentación visual al usuario.

---

#### 🔄 Pasos para Reproducir
1. Abrir la aplicación E-Commerce en el navegador.
2. Hacer clic en la barra de búsqueda del catálogo principal.
3. Ingresar la cadena de texto: `xyz123999`.
4. Presionar la tecla `Enter` o el icono de la lupa.

---

#### ⚖️ Comportamiento
* **Resultado Esperado:** La aplicación debe capturar el estado vacío y desplegar un componente con el mensaje: *"No se encontraron productos coincidentes con tu búsqueda"*, manteniendo los filtros activos.
* **Resultado Obtención (Actual):** La grilla de productos se limpia completamente, dejando un contenedor blanco sin ningún tipo de alerta o mensaje de estado.

---

#### 💻 Logs / Evidencia Técnica (DevTools Console)
```text
[Console Warning] Search query 'xyz123999' returned 0 items.
[UI Error] Uncaught TypeError: Cannot read properties of undefined (reading 'length') at ProductGrid.jsx:42
```
#### 💡 Sugerencia de Corrección para Desarrollo
Agregar un *Fallback Component* en React/Angular que valide si `products.length === 0` antes de renderizar la lista, mostrando la vista por defecto de *Empty State*.