win_form.py: adaptar los campos (ej. en vez de “Nombre” y “Edad”, usar “Correo”, “Ciudad”, etc.).

Cambios realizados:

- Campos del formulario → se añadieron Edad (años) y Estatura (cm) además de los que ya estaban (Correo, Ciudad, Pasos, Peso).

- Validación de datos → si algún campo está vacío, aparece un error; si todo está completo, se muestra un popup con el resumen.

- Botón Avanzar → se agregó un botón azul que cierra esta ventana y abre automáticamente win_list.py.

- Función abrir_win_list() → implementada con subprocess y sys.executable para ejecutar el archivo win_list.py en el mismo intérprete de Python.

- Organización visual → la ventana ahora tiene un tamaño ajustado (400x380), todos los campos están alineados y los botones quedan ordenados en la parte inferior.


<img width="397" height="408" alt="image" src="https://github.com/user-attachments/assets/1a446fdf-7aab-4cfc-ac06-1c44ae222c1b" />


import tkinter as tk
from tkinter import messagebox
import subprocess
import sys
import os

def guardar_datos():
    correo = entry_correo.get()
    ciudad = entry_ciudad.get()
    edad = entry_edad.get()
    estatura = entry_estatura.get()
    pasos = entry_pasos.get()
    peso = entry_peso.get()

    if not correo or not ciudad or not edad or not estatura or not pasos or not peso:
        messagebox.showerror("Error", "⚠️ Por favor, llena todos los campos.")
    else:
        messagebox.showinfo("Datos guardados",
                            f"✅ Registro exitoso:\n\n"
                            f"Correo: {correo}\n"
                            f"Ciudad: {ciudad}\n"
                            f"Edad: {edad} años\n"
                            f"Estatura: {estatura} cm\n"
                            f"Pasos: {pasos}\n"
                            f"Peso: {peso} kg")

def abrir_win_list():
    """Cierra esta ventana y abre win_list.py"""
    ventana.destroy()
    ruta = os.path.join(os.path.dirname(__file__), "win_list.py")
    subprocess.Popen([sys.executable, ruta])

# Crear ventana principal
ventana = tk.Tk()
ventana.title("Formulario de Registro - App Adultos Mayores")
ventana.geometry("400x380")

# Etiquetas y campos
tk.Label(ventana, text="Correo:").grid(row=0, column=0, padx=10, pady=5, sticky="w")
entry_correo = tk.Entry(ventana, width=30)
entry_correo.grid(row=0, column=1, padx=10, pady=5)

tk.Label(ventana, text="Ciudad:").grid(row=1, column=0, padx=10, pady=5, sticky="w")
entry_ciudad = tk.Entry(ventana, width=30)
entry_ciudad.grid(row=1, column=1, padx=10, pady=5)

tk.Label(ventana, text="Edad (años):").grid(row=2, column=0, padx=10, pady=5, sticky="w")
entry_edad = tk.Entry(ventana, width=30)
entry_edad.grid(row=2, column=1, padx=10, pady=5)

tk.Label(ventana, text="Estatura (cm):").grid(row=3, column=0, padx=10, pady=5, sticky="w")
entry_estatura = tk.Entry(ventana, width=30)
entry_estatura.grid(row=3, column=1, padx=10, pady=5)

tk.Label(ventana, text="Pasos del día:").grid(row=4, column=0, padx=10, pady=5, sticky="w")
entry_pasos = tk.Entry(ventana, width=30)
entry_pasos.grid(row=4, column=1, padx=10, pady=5)

tk.Label(ventana, text="Peso (kg):").grid(row=5, column=0, padx=10, pady=5, sticky="w")
entry_peso = tk.Entry(ventana, width=30)
entry_peso.grid(row=5, column=1, padx=10, pady=5)

# Botones
btn_guardar = tk.Button(ventana, text="Guardar", command=guardar_datos, bg="green", fg="white")
btn_guardar.grid(row=6, column=0, padx=10, pady=20)

btn_cancelar = tk.Button(ventana, text="Cancelar", command=ventana.quit, bg="red", fg="white")
btn_cancelar.grid(row=6, column=1, padx=10, pady=20)

btn_avanzar = tk.Button(ventana, text="Avanzar", command=abrir_win_list, bg="blue", fg="white")
btn_avanzar.grid(row=7, column=0, columnspan=2, pady=10)

ventana.mainloop()
