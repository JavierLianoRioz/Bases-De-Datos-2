## Ejercicio 1 — Modificación simple con \$set

### Enunciado

En la colección `cursos`, actualizar el curso "Programación Web" para:

* Cambiar el profesor a "Dra. Martínez"
* Marcar el curso como activo

### Respuesta

```js
db.cursos.updateOne(
  { nombre: "Programación Web" },
  { 
    $set: { 
      profesor: "Dra. Martínez",
      activo: true
    }
  }
)
```

### Justificación

* Uso de actualización parcial
* No se reescribe el documento completo
* Se modifican múltiples campos en una sola operación

## Ejercicio 2 — Incremento controlado con \$inc

### Enunciado

En la colección `cursos`, aumentar en 1 crédito todos los cursos cuyo nivel sea "Avanzado".

### Respuesta

```js
db.cursos.updateMany(
  { nivel: "Avanzado" },
  { $inc: { creditos: 1 } }
)
```

### Justificación

* Uso de updateMany
* Operación atómica por documento
* Evita leer y recalcular manualmente

## Ejercicio 3 — Manipulación de arrays con \$push

### Enunciado

Agregar el estudiante "Laura" al curso "Bases de Datos".

### Respuesta

```js
db.cursos.updateOne(
  { nombre: "Bases de Datos" },
  { $push: { estudiantes: "Laura" } }
)

```

### Justificación

* Uso de operador específico para arrays
* No se sobrescribe el array completo
* Permite crecimiento dinámico

