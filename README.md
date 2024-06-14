# Projeto de Análise e Simulação de Corridas da Fórmula E

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
