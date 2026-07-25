# 🧪 Matriz de Casos de Prueba (Test Cases Matrix)
**Proyecto:** E-Commerce Platform  
**Documento Relacionado:** [Plan de Pruebas](TEST_PLAN.md)  
**Estado:** Ejecutado  

---

## 🔑 Módulo 1: Autenticación de Usuarios

| ID | Título del Caso | Precondición | Pasos de Ejecución | Datos de Prueba | Resultado Esperado | Tipo | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-AUTH-01** | Login exitoso con credenciales válidas | Usuario registrado previamente | 1. Ir a /login<br>2. Ingresar usuario y contraseña<br>3. Clic en "Iniciar Sesión" | User: `mor_2314`<br>Pass: `83r5^_` | Redirección al Home y token de sesión generado en `localStorage`. | Functional (Happy Path) | **PASS** |
| **TC-AUTH-02** | Login fallido con contraseña incorrecta | Ninguna | 1. Ir a /login<br>2. Ingresar usuario válido y contraseña errónea<br>3. Clic en "Iniciar Sesión" | User: `mor_2314`<br>Pass: `wrongpass` | Muestra mensaje: *"Credenciales inválidas"* y permanece en la página. | Functional (Unhappy Path) | **PASS** |
| **TC-AUTH-03** | Validación de campos obligatorios en Login | Ninguna | 1. Ir a /login<br>2. Dejar campos vacíos<br>3. Clic en "Iniciar Sesión" | N/A | El botón de envío está deshabilitado o muestra bordes rojos indicando requerimiento. | UI / Validation | **PASS** |

---

## 🛒 Módulo 2: Carrito de Compras

| ID | Título del Caso | Precondición | Pasos de Ejecución | Datos de Prueba | Resultado Esperado | Tipo | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-CART-01** | Agregar producto existente al carrito | Usuario autenticado | 1. Navegar al catálogo<br>2. Seleccionar un producto<br>3. Clic en "Agregar al Carrito" | Product ID: `1` | El contador del carrito en el header se incrementa en +1. | Functional (Happy Path) | **PASS** |
| **TC-CART-02** | Modificar cantidad de items en el carrito | Producto agregado al carrito | 1. Ir al carrito<br>2. Cambiar cantidad de 1 a 5 unidades | Qty: `5` | El subtotal del producto y el total general se recalculan automáticamente. | Functional (Business) | **PASS** |
| **TC-CART-03** | Límite de cantidad negativa o cero | Producto en el carrito | 1. Ir al carrito<br>2. Intentar escribir `-1` o `0` en la cantidad | Qty: `-1` | El sistema no permite el valor o ajusta la cantidad automáticamente a 1 o elimina el item. | Edge Case | **PASS** |

---

## 🔍 Módulo 3: Catálogo y Búsqueda

| ID | Título del Caso | Precondición | Pasos de Ejecución | Datos de Prueba | Resultado Esperado | Tipo | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-CAT-01** | Filtrar productos por categoría | Catálogo cargado | 1. Ir a la vista principal<br>2. Seleccionar filtro "Electronics" | Category: `electronics` | La lista muestra únicamente productos pertenecientes a esa categoría. | Functional | **PASS** |
| **TC-CAT-02** | Búsqueda sin resultados coincidentes | Ninguna | 1. Ingresar texto aleatorio en la barra de búsqueda | Search: `xyz123999` | Muestra el mensaje *"No se encontraron productos coincidentes"*. | Functional (Unhappy Path) | **FAIL** *(Ver BUG-01)* |