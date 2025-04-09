# Calculadora-de-peso
import tkinter as tk
from tkinter import messagebox

def calcular_imc():
    try:
        peso = float(entry_peso.get())
        altura = float(entry_altura.get())
        imc = peso / (altura ** 2)
        resultado = f"IMC: {imc:.2f}\nClassificação: {classificar_imc(imc)}"
        label_resultado.config(text=resultado)
    except ValueError:
        messagebox.showerror("Erro", "Digite valores válidos para peso e altura.")

def classificar_imc(imc):
    if imc < 18.5:
        return "Abaixo do peso"
    elif 18.5 <= imc < 24.9:
        return "Peso normal"
    elif 25 <= imc < 29.9:
        return "Sobrepeso"
    elif 30 <= imc < 34.9:
        return "Obesidade grau 1"
    elif 35 <= imc < 39.9:
        return "Obesidade grau 2"
    else:
        return "Obesidade grau 3 (mórbida)"

# Janela principal
janela = tk.Tk()
janela.title("Calculadora de IMC")
janela.geometry("300x250")
janela.resizable(False, False)

# Widgets
tk.Label(janela, text="Peso (kg):").pack(pady=5)
entry_peso = tk.Entry(janela)
entry_peso.pack()

tk.Label(janela, text="Altura (m):").pack(pady=5)
entry_altura = tk.Entry(janela)
entry_altura.pack()

btn_calcular = tk.Button(janela, text="Calcular IMC", command=calcular_imc)
btn_calcular.pack(pady=10)

label_resultado = tk.Label(janela, text="", font=("Arial", 12))
label_resultado.pack(pady=10)

# Inicia o programa
janela.mainloop()
