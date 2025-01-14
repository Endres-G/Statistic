# Análise de Regressão Linear em R: Relação entre Ibovespa e Taxa Selic

## Visão Geral
Este projeto tem como objetivo estudar a relação entre o **índice Ibovespa** e a **taxa Selic** utilizando técnicas de **regressão linear** implementadas em R. A análise busca identificar como variações na taxa Selic podem impactar o principal índice da bolsa de valores brasileira, o Ibovespa.

---

## Motivação
O Ibovespa é amplamente utilizado como indicador do desempenho do mercado de ações no Brasil, enquanto a taxa Selic desempenha um papel crucial na política monetária do país. Compreender essa relação pode fornecer insights valiosos sobre como decisões econômicas afetam o mercado financeiro.

---

## Ferramentas e Tecnologias
- **Linguagem de Programação:** R
- **Bibliotecas Principais:**
  - `e1071`: Para análise estatística (assimetria e curtose).
  - `ggplot2`: Para visualização de dados.
  - `stats`: Para modelagem de regressão linear.
- **Editor de Código:** RStudio ou outro editor de sua preferência.

---

## Etapas do Projeto

### 1. **Coleta de Dados**
Os dados históricos do índice Ibovespa e da taxa Selic foram obtidos de fontes confiáveis, como:
- **Ibovespa:** B3 (Bolsa de Valores do Brasil).
- **Taxa Selic:** Banco Central do Brasil.

### 2. **Preparação dos Dados**
- Tratamento de valores ausentes ou inconsistentes.
- Alinhamento de períodos para garantir comparabilidade entre as séries temporais.

### 3. **Análise Exploratória de Dados (EDA)**
- Estatísticas descritivas (média, mediana, desvio padrão, assimetria e curtose).
- Visualizações iniciais, como gráficos de dispersão e histogramas, para identificar padrões.

### 4. **Modelagem de Regressão Linear**
- Fórmula: `Ibovespa ~ Taxa Selic`
- Ajuste do modelo utilizando a função `lm()` em R:
  ```R
  modelo <- lm(Ibovespa ~ Selic, data = dados)
  summary(modelo)
  ```
- Avaliação do modelo por meio de métricas como **R²** e **p-valores**.

### 5. **Visualização dos Resultados**
- Gráficos de regressão com `ggplot2`:
  ```R
  library(ggplot2)
  ggplot(dados, aes(x = Selic, y = Ibovespa)) +
    geom_point() +
    geom_smooth(method = "lm", col = "blue") +
    labs(title = "Regressão Linear: Ibovespa vs Taxa Selic",
         x = "Taxa Selic (%)",
         y = "Ibovespa")
  ```

### 6. **Interpretação dos Resultados**
Análise dos coeficientes estimados e discussão sobre a significância estatística da relação entre as variáveis.

---

## Resultados Esperados
- Compreender se existe uma relação linear significativa entre a taxa Selic e o Ibovespa.
- Identificar a direção e a magnitude dessa relação (se a taxa Selic aumenta, o Ibovespa tende a subir ou cair).

---

## Estrutura do Projeto
```
|-- dados/
|   |-- ibovespa.csv       # Dados históricos do Ibovespa
|   |-- selic.csv          # Dados históricos da taxa Selic
|
|-- scripts/
|   |-- analise_eda.R      # Análise exploratória de dados
|   |-- regressao_linear.R # Modelagem de regressão linear
|
|-- resultados/
|   |-- graficos/          # Visualizações geradas
|   |-- relatorio.pdf      # Relatório final
|
|-- README.md              # Documentação do projeto
```

---

## Como Executar

### Pré-requisitos
Certifique-se de ter o R instalado e as bibliotecas necessárias configuradas:
```R
install.packages(c("e1071", "ggplot2"))
```

### Passos
1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/projeto-regressao-ibovespa-selic.git
   cd projeto-regressao-ibovespa-selic
   ```

2. Execute o script de análise no R:
   ```R
   source("scripts/analise_eda.R")
   source("scripts/regressao_linear.R")
   ```

3. Os resultados estarão disponíveis na pasta `resultados/`.

---

## Contribuições
Sinta-se à vontade para abrir issues ou enviar pull requests. Toda ajuda para melhorar a análise é bem-vinda!

---

## Contato
- **Autor:** Gabriel Endres
- **Email:** gabriel.endres@example.com
- **GitHub:** [seu-usuario](https://github.com/seu-usuario)

