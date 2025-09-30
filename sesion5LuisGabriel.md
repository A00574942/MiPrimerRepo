Nombre del integrante y ventana asignada

Integrante: Luis Gabriel Aranda Torres

Ventana asignada: win_table.py (Tabla)

Lista de cambios aplicados a la ventana

Cambié las columnas originales (nombre, valor1, valor2) por las que necesita nuestro proyecto: fecha, pasos, peso.

Implementé que la ventana lea y escriba en el archivo src/data/health_log.csv, que guarda los registros de actividad.

Hice que el programa cree automáticamente un CSV de ejemplo si no existe, para que la tabla siempre tenga datos y no marque error.

Añadí un sistema de colores:

Rojo claro → cuando los pasos son menores a 7000 (alerta).

Verde claro → cuando los pasos son mayores o iguales a 7000 (meta cumplida).

Gris claro → para alternar filas y mejorar la legibilidad.

Ajusté el tamaño de la ventana y las columnas para que la información sea clara y visible.
