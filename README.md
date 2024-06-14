# Projeto de Análise e Simulação de Corridas da Fórmula E

## Equipe Responsável
- Isadora de Morais Meneghetti (RM556326)
- Júlio César Ruiz Zequin (RM554676)
- Kaio Drago Lima Souza (RM556095)
- Khadija do Rocio Vieira de Lima (RM558971)
- Pedro Henrique Faim dos Santos (RM557440)

Este projeto em Python coleta, processa e exibe dados sobre corridas da Fórmula E. O programa permite a inserção de dados de corridas, calcula a média de pontos das equipes, identifica o time vencedor e exibe os resultados de forma interativa.

## Funcionalidades

- Coleta de dados de corridas da Fórmula E.
- Cálculo da média de pontos das equipes.
- Identificação do time vencedor.
- Exibição dos resultados de cada corrida.
- Menu interativo para adicionar corridas e visualizar resultados.

## Estrutura do Projeto

O projeto é composto por funções bem definidas que seguem boas práticas de programação. Abaixo está a estrutura das principais funções:

- `get_race_data()`: Coleta os dados de uma corrida.
- `calculate_average_points(race_data)`: Calcula a média de pontos de uma corrida.
- `find_winning_team(race_data)`: Encontra o time com maior pontuação.
- `display_results(race_data)`: Exibe os resultados de uma corrida.
- `add_race()`: Adiciona uma nova corrida e exibe seus resultados.
- `show_menu()`: Exibe o menu de opções do programa.
- `main()`: Função principal que controla o fluxo do programa.

## Requisitos

- Python 3.x

## Como Executar

1. Clone este repositório ou faça o download do arquivo `formula_e.py`.
2. Execute o arquivo `formula_e.py`:

```bash
python formula_e.py

## Exemplo de uso

Menu:
1. Adicionar nova corrida
2. Exibir todas as corridas
3. Sair
Escolha uma opção: 1
Quantos times participaram da corrida? 3
Nome do time 1: Equipe A
Pontos do time Equipe A: 25
Nome do time 2: Equipe B
Pontos do time Equipe B: 18
Nome do time 3: Equipe C
Pontos do time Equipe C: 30

Resultados da Corrida:
A média de pontos foi: 24.33
O time vencedor foi: Equipe C com 30 pontos

Menu:
1. Adicionar nova corrida
2. Exibir todas as corridas
3. Sair
Escolha uma opção: 2

Corrida 1:
A média de pontos foi: 24.33
O time vencedor foi: Equipe C com 30 pontos

Menu:
1. Adicionar nova corrida
2. Exibir todas as corridas
3. Sair
Escolha uma opção: 3
Saindo...


## Estrutura do código

def get_race_data():
    """Coleta os dados de uma corrida da Fórmula E"""
    race_data = []
    number_of_teams = int(input("Quantos times participaram da corrida? "))

    for i in range(number_of_teams):
        team_name = input(f"Nome do time {i+1}: ")
        points = int(input(f"Pontos do time {team_name}: "))
        race_data.append((team_name, points))

    return race_data

def calculate_average_points(race_data):
    """Calcula a média de pontos de uma corrida"""
    total_points = sum(points for _, points in race_data)
    average_points = total_points / len(race_data)
    return average_points

def find_winning_team(race_data):
    """Encontra o time com maior pontuação"""
    winning_team = max(race_data, key=lambda team: team[1])
    return winning_team

def display_results(race_data):
    """Exibe os resultados de uma corrida"""
    average_points = calculate_average_points(race_data)
    winning_team = find_winning_team(race_data)

    print("\nResultados da Corrida:")
    print(f"A média de pontos foi: {average_points:.2f}")
    print(f"O time vencedor foi: {winning_team[0]} com {winning_team[1]} pontos")

all_races = []

def add_race():
    """Adiciona uma nova corrida e exibe seus resultados"""
    race_data = get_race_data()
    all_races.append(race_data)
    display_results(race_data)

def show_menu():
    """Exibe o menu de opções do programa"""
    print("\nMenu:")
    print("1. Adicionar nova corrida")
    print("2. Exibir todas as corridas")
    print("3. Sair")

def main():
    """Função principal que controla o fluxo do programa"""
    while True:
        show_menu()
        choice = input("Escolha uma opção: ")

        if choice == '1':
            add_race()
        elif choice == '2':
            for i, race in enumerate(all_races):
                print(f"\nCorrida {i+1}:")
                display_results(race)
        elif choice == '3':
            print("Saindo...")
            break
        else:
            print("Opção inválida, tente novamente.")

if __name__ == '__main__':
    main()






