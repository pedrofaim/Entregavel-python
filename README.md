# Simulador de Fórmula E

Este é um jogo simples de corrida de Fórmula E desenvolvido em Python usando a biblioteca Pygame. O jogador controla um carro que deve desviar dos obstáculos em uma pista infinita, acumulando pontos à medida que evita os obstáculos.

## Requisitos

- Python 3.x
- Pygame

## Instalação

1. **Clone este repositório** ou baixe os arquivos diretamente.

2. **Instale as dependências** necessárias. Você pode usar `pip` para instalar Pygame:
    ```bash
    pip install pygame
    ```

3. **Adicione as imagens**:
   - Certifique-se de ter duas imagens: `pista.png` (imagem da pista) e `carro.png` (imagem do carro).
   - Coloque essas imagens no mesmo diretório onde o script Python (`main.py`) está localizado.

## Como jogar

1. **Execute o script Python**:
    ```bash
    python main.py
    ```

2. **Controles do jogo**:
   - Use a tecla **esquerda** (`←`) para mover o carro para a esquerda.
   - Use a tecla **direita** (`→`) para mover o carro para a direita.

3. **Objetivo do jogo**:
   - Desviar dos obstáculos que aparecem na pista.
   - Acumular pontos à medida que o carro evita os obstáculos.

## Estrutura do código

- `main.py`: Script principal que contém toda a lógica do jogo.
- `pista.png`: Imagem de fundo da pista.
- `carro.png`: Imagem do carro do jogador.

## Exemplo de Código

Aqui está um trecho do código principal:

```python
import pygame
import random
import os

pygame.init()

# Resolução da janela
width = 800
height = 600
tamanho_tela = (width, height)
tela = pygame.display.set_mode(tamanho_tela)
pygame.display.set_caption('Simulador de Fórmula E')

# Função para carregar imagem com tratamento de erro
def carregar_imagem(caminho):
    if not os.path.exists(caminho):
        print(f"Erro: arquivo {caminho} não encontrado.")
        pygame.quit()
        exit()
    try:
        imagem = pygame.image.load(caminho)
        return imagem
    except pygame.error as e:
        print(f"Erro ao carregar imagem {caminho}: {e}")
        pygame.quit()
        exit()

# Caminho para as imagens (modifique conforme necessário)
caminho_pista = os.path.join('C:\\Users\\Gamer\\Downloads\\vinheris\\GS-python\\static', 'pista.png')
caminho_carro = os.path.join('C:\\Users\\Gamer\\Downloads\\vinheris\\GS-python\\static', 'carro.png')

# Carregar imagens
pista_img = carregar_imagem(caminho_pista)
carro_img = carregar_imagem(caminho_carro)
carro_img = pygame.transform.scale(carro_img, (50, 100))  # Redimensiona a imagem do carro

# Configurações do funcionamento
voce_perdeu = False
speed = 5
score = 0

# Carro do jogador
carro_width = 50
carro_height = 100
carro_x = width // 2 - carro_width // 2
carro_y = height - carro_height - 20
carro_velocidade = 10

# Obstáculos
obstaculos = []
obstaculo_width = 50
obstaculo_height = 100
obstaculo_velocidade = 5

# Função para gerar obstáculos
def gerar_obstaculo():
    x = random.randint(150, 650 - obstaculo_width)
    y = -obstaculo_height
    obstaculos.append([x, y])

# Função para desenhar o carro
def desenhar_carro(x, y):
    tela.blit(carro_img, (x, y))

# Função para desenhar os obstáculos
def desenhar_obstaculos(obstaculos):
    for obstaculo in obstaculos:
        pygame.draw.rect(tela, (200, 0, 0), (obstaculo[0], obstaculo[1], obstaculo_width, obstaculo_height))

# Função para exibir o score
def mostrar_score(score):
    font = pygame.font.Font(None, 36)
    text = font.render("Score: " + str(score), True, (255, 255, 255))
    tela.blit(text, (10, 10))

# ------------------------------------------------------------------LOOP-----------------------------------------------------------------------
tempo = pygame.time.Clock()
fps = 60
correndo = True

while correndo:
    tempo.tick(fps)

    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            correndo = False

    # Movimento do carro
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and carro_x > 150:
        carro_x -= carro_velocidade
    if keys[pygame.K_RIGHT] and carro_x < 650 - carro_width:
        carro_x += carro_velocidade

    # Atualizar posição dos obstáculos
    for obstaculo in obstaculos:
        obstaculo[1] += obstaculo_velocidade

    # Remover obstáculos fora da tela e incrementar score
    for obstaculo in obstaculos:
        if obstaculo[1] > height:
            score += 1
            obstaculos.remove(obstaculo)

    # Gerar novos obstáculos
    if random.randint(1, 60) == 1:
        gerar_obstaculo()

    # Verificar colisões
    for obstaculo in obstaculos:
        if (carro_y < obstaculo[1] + obstaculo_height and
            carro_y + carro_height > obstaculo[1] and
            carro_x < obstaculo[0] + obstaculo_width and
            carro_x + carro_width > obstaculo[0]):
            voce_perdeu = True
            correndo = False

    # Elementos (desenhos e atualizações)
    # Desenhar pista
    tela.blit(pista_img, (0, 0))

    # Desenhar o carro e os obstáculos
    desenhar_carro(carro_x, carro_y)
    desenhar_obstaculos(obstaculos)
    mostrar_score(score)

    pygame.display.update()

pygame.quit()

if voce_perdeu:
    print("Você perdeu! Seu score foi:", score)
