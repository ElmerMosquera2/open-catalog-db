# 🛒 Open Catalog db

Infraestructura de datos abiertos para el registro universal de productos en Colombia. El objetivo es proveer una base de datos maestra (Master Data).

## 🚀 Arquitectura y Concepto de Datos
Este repositorio sigue un enfoque NoSQL y basado en grafos, donde cada producto es un nodo y las relaciones entre ellos (ej. "compatible con", "mismo fabricante") se gestionan centralmente.

## 📂 Estructura del Repositorio
Los datos están segmentados por categoría para optimizar la sincronización y la gestión de Pull Requests:

- /data: Contiene archivos JSON por categoría (ej. mecatos.json, aseo-personal.json).
- catalog-manifest.json: El índice global que define las categorías y sus atributos de extensión requeridos.
- schema-v1.json: El contrato de datos que valida la estructura de cada producto.
- LICENSE: Define los términos legales de uso de esta base de datos.

## 📝 Estándar de Solicitud de Producto


Los colaboradores deben seguir la estructura definida en schema-v1.json. El objeto base del producto se enfoca en la identidad y la clasificación:
```json
{
  "codigo": "string (EAN-13, UPC o SKU)",
  "nombre": "string",
  "marca": "string",
  "id_categoria": "string (ej: lacteos-huevos)",
  "categories": {
    // Atributos extra condicionales (ej. peso, ram, talla)
  }
}
```
## Sistema de Extensión de Atributos
Utilizamos un sistema de extensión condicional. Dependiendo su categoria, se requieren campos extra específicos que se agrupan en el objeto categories. Consulta catalog-manifest.json para ver qué campos extra son obligatorios para cada categoría.

## 🤝 Cómo Colaborar (Pull Requests)
Identifica el archivo JSON correcto dentro de /data/ para tu producto.
Añade tu producto siguiendo estrictamente el estándar de schema-v1.json.
Abre un Pull Request.

**Importante:**
- No se aceptan datos personales (correos, teléfonos, nombres de contactos).
- No se aceptan precios ni stock, esa es información local de cada tienda.
- Las relaciones son gestianas por la comunidad administradora para mantener la integridad de la red de datos.

## ⚖️ Aviso Legal y Privacidad (Colombia 2026)
Este repositorio cumple con la Ley 1581 de 2012 (Habeas Data) y el Estatuto del Consumidor (Ley 1480 de 2011) en Colombia. Los datos son públicos, de uso libre bajo la licencia LICENSE del repositorio.
