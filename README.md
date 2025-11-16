import tkinter as tk
from time import strftime
import os

# Caminho do ícone (para evitar erros ao virar .exe)
icon_path = os.path.join(os.path.dirname(__file__), "icon.ico")

# Janela principal
janela = tk.Tk()
janela.title("Relógio - Dark Mode")
janela.geometry("350x150")
janela.resizable(False, False)
janela.configure(bg="#0d0d0d")  # dark mode real

# Definir ícone, se existir
if os.path.exists(icon_path):
    janela.iconbitmap(icon_path)

# Estilo do relógio
label_tempo = tk.Label(
    janela,
    font=("Consolas", 42, "bold"),
    background="#0d0d0d",
    foreground="#00eaff"
)
label_tempo.pack(pady=6)

label_data = tk.Label(
    janela,
    font=("Consolas", 14),
    background="#0d0d0d",
    foreground="#ffffff"
)
label_data.pack()

# Função de atualização
def atualizar():
    label_tempo.config(text=strftime("%H:%M:%S"))
    label_data.config(text=strftime("%d/%m/%Y"))
    label_tempo.after(1000, atualizar)

atualizar()
janela.mainloop()
