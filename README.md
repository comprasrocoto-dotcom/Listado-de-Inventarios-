# Sistema de Inventarios — Rocoto · Hot Wings · Malanga

Página web de conteo de inventario. Lee los archivos Excel directamente — **no requiere conversión ni código**.

---

## Estructura del proyecto

```
inventarios-app/
├── index.html                      ← La app web (no modificar)
├── README.md
└── inventarios/
    ├── ROCOTO.xlsx                 ← Reemplaza este cuando haya cambios
    ├── HOT_WINGS.xlsx
    └── MALANGA.xlsx
```

---

## ✅ Cómo actualizar cuando hay cambios en los insumos

Solo necesitas **reemplazar el archivo Excel** en GitHub. Son 3 pasos:

### Opción A — Desde el navegador en GitHub.com (más fácil)

1. Entra a tu repositorio en GitHub
2. Haz clic en la carpeta **`inventarios/`**
3. Haz clic sobre el archivo que quieres actualizar (ej: `ROCOTO.xlsx`)
4. Haz clic en el ícono **`...`** (arriba a la derecha) → **"Upload file"** o **"Delete file"**
   - O directamente: arrastra el nuevo archivo encima del nombre
5. Confirma con **"Commit changes"**

La página web se actualiza automáticamente en menos de 1 minuto. ✓

---

### Opción B — Desde la terminal con Git

```bash
# Copia el Excel nuevo a la carpeta inventarios/
cp ~/Descargas/FORMATO_DE_INVENTARIOS_ROCOTO.xlsx inventarios/ROCOTO.xlsx

# Sube el cambio a GitHub
git add inventarios/ROCOTO.xlsx
git commit -m "Actualizar inventario Rocoto - Junio 2025"
git push
```

---

## ➕ Cómo agregar una nueva marca

1. Pon el Excel nuevo en la carpeta `inventarios/` con un nombre sin espacios.
   Ejemplo: `inventarios/NUEVA_MARCA.xlsx`

2. Abre `index.html` y busca esta sección (líneas ~60):

```javascript
const MARCAS = [
  { nombre: 'Rocoto',    archivo: 'inventarios/ROCOTO.xlsx'    },
  { nombre: 'Hot Wings', archivo: 'inventarios/HOT_WINGS.xlsx' },
  { nombre: 'Malanga',   archivo: 'inventarios/MALANGA.xlsx'   },
];
```

3. Agrega la nueva marca:

```javascript
const MARCAS = [
  { nombre: 'Rocoto',      archivo: 'inventarios/ROCOTO.xlsx'      },
  { nombre: 'Hot Wings',   archivo: 'inventarios/HOT_WINGS.xlsx'   },
  { nombre: 'Malanga',     archivo: 'inventarios/MALANGA.xlsx'     },
  { nombre: 'Nueva Marca', archivo: 'inventarios/NUEVA_MARCA.xlsx' }, // ← nueva
];
```

4. Sube los cambios a GitHub.

---

## 🌐 Publicar en GitHub Pages

1. En GitHub: **Settings → Pages**
2. Source: rama `main`, carpeta `/ (root)`
3. Guardar → en ~1 minuto el sitio estará en:
   `https://tu-usuario.github.io/nombre-repositorio`

---

## ¿Qué formato debe tener el Excel?

La página lee automáticamente el formato original. Solo necesita que el Excel tenga estas columnas en orden:

| Columna 1   | Columna 2    | Columna 3 | Columna 4   |
|-------------|--------------|-----------|-------------|
| Subfamilia  | Cód. Barras  | Artículo  | SubartÍculo |
| ABARROTES   | ABA001       | ACEITE... | GRAMOS      |

Si el proveedor cambia el formato del Excel, avisa para ajustar el lector.
