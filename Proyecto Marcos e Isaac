import tkinter as tk
from tkinter import ttk
from tkinter import messagebox

class LigaEspanolaApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Gestión de Equipos - Liga Española")
        self.root.geometry("800x600")
        
        # Crear barra de menú
        self.menu_bar = tk.Menu(self.root)
        self.root.config(menu=self.menu_bar)
        
        # Menú de archivo
        archivo_menu = tk.Menu(self.menu_bar, tearoff=0)
        archivo_menu.add_command(label="Nuevo Equipo", command=self.nuevo_equipo)
        archivo_menu.add_separator()
        archivo_menu.add_command(label="Salir", command=self.root.quit)
        self.menu_bar.add_cascade(label="Archivo", menu=archivo_menu)
        
        # Menú de ayuda
        ayuda_menu = tk.Menu(self.menu_bar, tearoff=0)
        ayuda_menu.add_command(label="Acerca de", command=self.mostrar_acerca_de)
        self.menu_bar.add_cascade(label="Ayuda", menu=ayuda_menu)
        
        # Notebook para gestionar pestañas
        self.notebook = ttk.Notebook(self.root)
        self.notebook.pack(expand=True, fill="both")
        
        # Pestaña inicial: lista de equipos
        self.tab_equipos = ttk.Frame(self.notebook)
        self.notebook.add(self.tab_equipos, text="Equipos")
        self.crear_tabla_equipos(self.tab_equipos)

    def crear_tabla_equipos(self, parent):
        """Crea una tabla para mostrar los equipos."""
        self.tree = ttk.Treeview(parent, columns=("Nombre", "Ciudad", "Estadio"), show="headings")
        self.tree.heading("Nombre", text="Nombre")
        self.tree.heading("Ciudad", text="Ciudad")
        self.tree.heading("Estadio", text="Estadio")
        self.tree.pack(expand=True, fill="both", padx=10, pady=10)
        
        # Datos de ejemplo
        equipos = [
            ("Real Madrid", "Madrid", "Santiago Bernabéu"),
            ("FC Barcelona", "Barcelona", "Camp Nou"),
            ("Atlético de Madrid", "Madrid", "Metropolitano"),
        ]
        for equipo in equipos:
            self.tree.insert("", "end", values=equipo)

    def nuevo_equipo(self):
        """Abre una ventana para agregar un nuevo equipo."""
        ventana_nuevo = tk.Toplevel(self.root)
        ventana_nuevo.title("Nuevo Equipo")
        ventana_nuevo.geometry("400x300")
        
        # Entradas de datos
        tk.Label(ventana_nuevo, text="Nombre del Equipo:").pack(pady=5)
        nombre_entry = tk.Entry(ventana_nuevo)
        nombre_entry.pack(pady=5)

        tk.Label(ventana_nuevo, text="Ciudad:").pack(pady=5)
        ciudad_entry = tk.Entry(ventana_nuevo)
        ciudad_entry.pack(pady=5)

        tk.Label(ventana_nuevo, text="Estadio:").pack(pady=5)
        estadio_entry = tk.Entry(ventana_nuevo)
        estadio_entry.pack(pady=5)

        def guardar_equipo():
            nombre = nombre_entry.get()
            ciudad = ciudad_entry.get()
            estadio = estadio_entry.get()
            if nombre and ciudad and estadio:
                self.tree.insert("", "end", values=(nombre, ciudad, estadio))
                ventana_nuevo.destroy()
            else:
                messagebox.showwarning("Advertencia", "Todos los campos son obligatorios.")

        # Botón para guardar
        tk.Button(ventana_nuevo, text="Guardar", command=guardar_equipo).pack(pady=20)

    def mostrar_acerca_de(self):
        """Muestra información sobre la aplicación."""
        messagebox.showinfo("Acerca de", "Gestión de Equipos - Liga Española\nVersión 1.0")

if __name__ == "__main__":
    root = tk.Tk()
    app = LigaEspanolaApp(root)
    root.mainloop()
