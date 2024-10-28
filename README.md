import random
import time

def generar_tarjeta_bingo():
    tarjeta = []
    columnas = ['B', 'I', 'N', 'G', 'O']
    for i in range(len(columnas)):
        if i == 2:  # La columna N tiene un espacio libre
            numeros = random.sample(range(1 + i * 15, 16 + i * 15), 4)
            numeros.insert(2, 'FREE')  # Espacio libre en la tarjeta
        else:
            numeros = random.sample(range(1 + i * 15, 16 + i * 15), 5)
        tarjeta.append(numeros)
    return tarjeta

def imprimir_tarjeta(tarjeta):
    print(" B   I   N   G   O")
    for i in range(5):
        for j in range(5):
            if j == 2 and i == 2:
                print("FREE", end=' ')
            else:
                print(f"{tarjeta[j][i]:<3}", end=' ')
        print()

def jugar_bingo():
    tarjeta = generar_tarjeta_bingo()
    imprimir_tarjeta(tarjeta)

    numeros_llamados = []
    numeros_disponibles = list(range(1, 76))  # Números del 1 al 75

    while numeros_disponibles:
        numero = random.choice(numeros_disponibles)
        numeros_disponibles.remove(numero)
        numeros_llamados.append(numero)
        print(f"Número llamado: {numero}")
        time.sleep(3)

        if input("¿Deseas continuar? (s/n): ").lower() != 's':
            break

if __name__ == "__main__":
    jugar_bingo()
