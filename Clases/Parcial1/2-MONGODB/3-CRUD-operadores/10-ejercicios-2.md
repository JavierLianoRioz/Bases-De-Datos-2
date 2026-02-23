## Ejercicio 4 — Eliminación selectiva con \$pull

### Enunciado

Eliminar al estudiante "Carlos" del curso "Bases de Datos".

### Respuesta

```js
db.cursos.updateOne(
  { nombre: "Bases de Datos" },
  { $pull: { estudiantes: "Carlos" } }
)

```

### Justificación

* Eliminación por coincidencia
* No requiere conocer índice del array
* Evita reconstrucción manual del array

## Ejercicio 5 — Actualización en documento embebido

### Enunciado

En la colección `pedidos`, cambiar la ciudad del cliente "Ana Pérez" a "Valencia".

### Respuesta

```js
db.pedidos.updateOne(
  { "cliente.nombre": "Ana Pérez" },
  { $set: { "cliente.ciudad": "Valencia" } }
)
```

### Justificación

* Uso de notación con punto
* Acceso a campos anidados
* Actualización precisa sin modificar otros subcampos

## Ejercicio 6 — Upsert con contador

### Enunciado

Registrar accesos diarios en colección `accesos`:

Si existe documento con:

* usuario: "ana"
* fecha: "2026-02-19"

Incrementar contador en 1.

Si no existe, crearlo con contador = 1.

### Respuesta

```js
db.accesos.updateOne(
  { usuario: "ana", fecha: "2026-02-19" },
  { $inc: { contador: 1 } },
  { upsert: true }
)
```

### Justificación

* Uso práctico de upsert
* Patrón común en sistemas reales
* Evita lógica adicional en aplicación

