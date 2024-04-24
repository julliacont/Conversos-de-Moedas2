python
import requests

def converter_moeda(valor, de, para):
    url = f'https://api.exchangerate-api.com/v4/latest/{de}'
    response = requests.get(url)
    data = response.json()
    taxa_conversao = data['rates'][para]
    valor_convertido = valor * taxa_conversao
    return valor_convertido

print("Bem-vindo ao Conversor de Moedas!")
print("Selecione a moeda de origem e a moeda de destino:")

moedas_disponiveis = ["USD", "EUR", "JPY", "BRL", "GBP", "CAD"]

for idx, moeda in enumerate(moedas_disponiveis):
    print(f"{idx+1}. {moeda}")

opcao_origem = int(input("Escolha a moeda de origem: "))
opcao_destino = int(input("Escolha a moeda de destino: "))
valor_a_converter = float(input("Digite o valor a ser convertido: "))

moeda_origem = moedas_disponiveis[opcao_origem - 1]
moeda_destino = moedas_disponiveis[opcao_destino - 1]

resultado = converter_moeda(valor_a_converter, moeda_origem, moeda_destino)

print(f"O valor convertido de {moeda_origem} para {moeda_destino} é: {resultado}")# Conversos-de-Moedas2
