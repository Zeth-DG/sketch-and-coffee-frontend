# Sketch & Coffee ☕✏️

Bienvenido al repositorio oficial de **Sketch & Coffee**, una cafetería que sale del papel al mundo 3D, combinando el amor por el café de especialidad con un espacio creativo para dibujar, diseñar y dejar volar la imaginación.

## Sobre el proyecto

Este es un proyecto colaborativo para desarrollar la página web de **Sketch & Coffee**.
El sitio tendrá como objetivo mostrar nuestro menú, ubicación, horarios, galería de espacios y promociones, así como integrar una experiencia visual que refleje la esencia artística y acogedora de la marca.

## Alcance de este repositorio

Este repositorio contiene **únicamente el frontend** del proyecto: las páginas HTML, los estilos y la lógica en JavaScript del catálogo, el menú interactivo, el carrito y los formularios.

También incluye, como entregable de la materia de base de datos, el script `Base_Datos_SQL_JSON/base_datos.sql` con el diseño relacional y los datos de muestra, además de los archivos JSON que alimentan el catálogo.

Aquí **no hay código Java ni configuración de Spring Boot**.

## Backend (repositorio aparte)

El backend se desarrolla en un repositorio independiente:

**https://github.com/Zeth-DG/sketch-and-coffee-backend**

Está construido con **Java, Spring Boot y MySQL**. Ahí viven la entidad `Usuario`, su repositorio, el controlador y la conexión a la base de datos. La API de usuarios se probó con Postman sobre la ruta `/sketchcoffee/usuarios`, que responde `200 OK` con los registros leídos desde MySQL.

El frontend de este repositorio todavía **no consume** esa API: el catálogo se arma desde archivos JSON y el carrito se guarda en `localStorage`. Conectar ambos lados es la siguiente etapa del proyecto.

## Base de datos

El script `Base_Datos_SQL_JSON/base_datos.sql` crea la base `sketch_coffee` con cinco tablas (`categorias`, `usuarios`, `productos`, `pedidos`, `detalles_pedido`), sus claves foráneas, restricciones y cinco registros de muestra por tabla.

> **Advertencia:** el script comienza con `DROP DATABASE`, por lo que solo debe ejecutarse sobre una base de demostración. Nunca sobre datos que se quieran conservar.

## Estructura de carpetas

```
sketch-and-coffee/
├── index.html                     Página de inicio
├── menu.html                      Catálogo con filtros, orden y paginación
├── menu-interactivo.html          Menú guiado por pasos y carrito
├── detalles_del_producto.html     Ficha de producto
├── creacion_de_producto.html      Alta de producto (solo administrador)
├── contacto.html                  Formulario de contacto con EmailJS
├── inicio-sesion.html             Inicio de sesión
├── registro.html                  Registro de usuarios
├── acerca_de_nosotros.html        Información de la marca
├── landingpromociones.html        Promociones
├── aviso.html                     Aviso de privacidad
├── terminos.html                  Términos y condiciones
│
├── componentes/                   Header, footer y carrito reutilizables
├── css/                           Hoja de estilos principal
├── js/                            Lógica del frontend
│   ├── menu-productos.js          Carga y normaliza los JSON del catálogo
│   ├── menu-filtros.js            Filtros, orden y paginación
│   ├── menu-interactivo.js        Menú por pasos (bebidas, platillos, crepas)
│   ├── carrito-menu-interactivo.js Carrito en localStorage
│   ├── formulario.js              Envío del formulario con EmailJS
│   ├── validaciones.js            Reglas de validación de campos
│   └── ...                        Sesión, header, footer, newsletter
│
├── imagenes/                      Recursos gráficos del sitio
│
├── menu/JSON documentos/
│   ├── menu.json                  Catálogo original (140 productos)
│   └── productos-extra.json       Productos complementarios
├── menu_interactivo/
│   └── menu_interactivo.json      Datos del menú interactivo
│
├── Base_Datos_SQL_JSON/
│   ├── base_datos.sql             Script DDL + DML de MySQL
│   ├── menu_sketch.json           Catálogo consolidado por categorías
│   ├── usuarios.json              Usuarios ficticios de prueba
│   └── Imagenes_BaseDatos/        Diagrama ER y capturas de evidencia
│
├── pruebasUnitariasValidacion/    Pruebas unitarias con Jest (59)
├── GUION-EXPOSICION.txt           Guion de la presentación del proyecto
└── package.json                   Dependencias del proyecto
```

## Estado del proyecto

| Parte | Estado |
|---|---|
| Frontend: catálogo, carrito, menú interactivo y formularios | Funcional, con datos desde JSON y `localStorage` |
| Modelo de base de datos (5 tablas) | Implementado y probado en MySQL |
| Backend Java: entidad, repositorio y API de usuarios | En desarrollo, en su propio repositorio |
| Integración frontend → API → MySQL | Siguiente etapa |

## Tecnologías utilizadas

- HTML5
- CSS3
- JavaScript
- EmailJS (envío del formulario de contacto)
- Jest (pruebas unitarias de validación)
- MySQL (modelo de datos)
- Java y Spring Boot (backend, en repositorio aparte)

## Cómo ejecutar el frontend

1. Clona este repositorio.
2. Abre el proyecto con Live Server. El puerto está configurado en `.vscode/settings.json` (5501).
3. Visita `index.html` desde el servidor local, no con doble clic: las páginas cargan datos con `fetch` y eso requiere HTTP.

El frontend funciona sin el backend, porque toma los datos de los archivos JSON. Para correr las pruebas unitarias:

```bash
cd pruebasUnitariasValidacion
npm install
npm test
```
