# Fantasy E - README

---

## Descrição do Projeto

O projeto **Fantasy E** visa aumentar a visibilidade e o engajamento dos fãs da Fórmula E no Brasil por meio do desenvolvimento de uma plataforma de fantasy sports. Esta plataforma permite que os usuários selecionem pilotos, formem suas equipes e ganhem pontos com base no desempenho real dos pilotos em corridas. Através de gráficos de análise de sensibilidade, cálculo de pontuação e projeções de crescimento de usuários, o projeto oferece uma experiência interativa e educativa para os entusiastas da Fórmula E.

---

## Funcionalidades

1. **Análise de Sensibilidade:**
   - Gráfico que mostra como diferentes fatores (vitórias, pole positions, voltas mais rápidas e posições finais) afetam a pontuação total.
   
2. **Cálculo de Pontuação dos Pilotos:**
   - Função que calcula a pontuação de cada piloto com base nos critérios definidos.
   
3. **Projeção de Crescimento de Usuários:**
   - Gráfico que projeta o crescimento do número de usuários da plataforma e consumidores da Fórmula E ao longo de 12 meses com base em uma taxa de crescimento mensal.

---

## Requisitos

Para executar os scripts do projeto, é necessário ter o Python instalado em sua máquina. A versão recomendada é a 3.6 ou superior.

---

## Dependências

As principais dependências para executar os scripts são:
- **numpy:** Para operações matemáticas e manipulação de arrays.
- **matplotlib:** Para a criação de gráficos.

Estas bibliotecas podem ser instaladas usando o pip:
```bash
pip install numpy matplotlib
```

---

## Instruções de Uso

### Gráfico de Análise de Sensibilidade

Este script gera um gráfico que mostra como diferentes fatores influenciam a pontuação total dos pilotos.

```python
import numpy as np
import matplotlib.pyplot as plt

# Instalando os Parâmetros
vitorias = np.linspace(0, 5, 100)
pole_positions = np.linspace(0, 5, 100)
voltas_mais_rapidas = np.linspace(0, 5, 100)
posicoes_finais = np.linspace(1, 10, 100)

# Função para Calcular Pontuação
def calcular_pontuacao_sensibilidade(vitoria, pole_position, volta_mais_rapida, posicao_final):
    pontos_vitoria = 25 * vitoria
    pontos_pole_position = 3 * pole_position
    pontos_volta_mais_rapida = 1 * volta_mais_rapida
    pontos_posicao_final = 0
    if 1 < posicao_final <= 10:
        pontos_posicao_final = [18, 15, 12, 10, 8, 6, 4, 2, 1][int(posicao_final - 2)]
    return pontos_vitoria + pontos_pole_position + pontos_volta_mais_rapida + pontos_posicao_final

# Resultados das Pontuações
pontuacoes_vitorias = [calcular_pontuacao_sensibilidade(v, 1, 1, 1) for v in vitorias]
pontuacoes_pole_positions = [calcular_pontuacao_sensibilidade(1, p, 1, 1) for p in pole_positions]
pontuacoes_voltas_mais_rapidas = [calcular_pontuacao_sensibilidade(1, 1, v, 1) for v in voltas_mais_rapidas]
pontuacoes_posicoes_finais = [calcular_pontuacao_sensibilidade(1, 1, 1, p) for p in posicoes_finais]

# Gráfico
plt.figure(figsize=(10, 6))
plt.plot(vitorias, pontuacoes_vitorias, label='Vitórias', color='blue')
plt.plot(pole_positions, pontuacoes_pole_positions, label='Pole Positions', color='green')
plt.plot(voltas_mais_rapidas, pontuacoes_voltas_mais_rapidas, label='Voltas Mais Rápidas', color='red')
plt.plot(posicoes_finais, pontuacoes_posicoes_finais, label='Posições Finais', color='orange')
plt.xlabel('Quantidade')
plt.ylabel('Pontuação Total')
plt.title('Análise de Sensibilidade da Pontuação')
plt.legend()
plt.grid(True)
plt.show()


Este script gera um gráfico que mostra como diferentes fatores influenciam a pontuação total dos pilotos.
```



