# Ganhos-mensais
//programa em py3 para computar e auxiliar a contabilidade mensal dos meus ganhos


import math


def atualizar_lista(dia):
    lista = []
    while True:
        entrada = input(f"Digite quanto ganhou na {dia} para adicionar à lista (ou 'sair' para finalizar): ")
        if entrada.lower() == 'sair':
            break
        try:
            numero = float(entrada)
            lista.append(numero)
        except ValueError:
            print("Por favor, insira um valor válido.")
    return lista

def somar_listas_dias_uteis():
    dias_uteis = ["segunda-feira", "terça-feira", "quarta-feira", "quinta-feira", "sexta-feira"]
    listas = {}
    total_geral = 0
    for dia in dias_uteis:
        listas[dia] = atualizar_lista(dia)
    for dia, lista in listas.items():
        soma = sum(lista)
        total_geral += soma
        print(f"Soma dos elementos para {dia}: {soma}")

    print(f"Soma total dos elementos de todos os dias: {total_geral}")

def calcular_total_mensal():
    totais_mensais = {}
    for i in range(1, 6):
        print(f"\nSemana {i}:")
        total_semanal = somar_listas_dias_uteis()
        totais_mensais[i] = total_semanal

    total_mensal = sum(totais_mensais.values())
    print("\nTotais semanais:", totais_mensais)
    print(f"Total mensal: {total_mensal}")


calcular_total_mensal()

