# Carregar os dados
dados = read.csv("ibovSelic.csv")
#só para ter as datas em variavel
date = dados[,1]

#dados das variaveis de fato
ibov = dados[,2]
selic = dados[,3]

#valor minimo de cada variavel
min_bov = min(ibov)
min_selic = min(selic)

#quartil1
q1_bov = quantile(ibov,0.25)
q1_selic = quantile(selic, 0.25)

#mediana
mediana_bov = median(ibov)
mediana_selic = median(selic)

#quartil3
q3_bov = quantile(ibov,0.75)
q3_selic = quantile(selic, 0.75)

#valor maximo
max_bov = max(ibov)
max_selic = max(selic)

#desvio interquartilico
desvio_inter_bov = q3_bov - q1_bov
desvio_inter_selic = q3_selic - q1_selic

#média aritmética
media_bov = mean(ibov)
media_selic = mean(selic)

#desvio padrão
desvio_bov = sd(ibov)
desvio_selic = sd(selic)

# Função para calcular o coeficiente de assimetria de Pearson
pearson = function(x) {
  me <- mean(x)       # Calcular a média
  m <- median(x)      # Calcular a mediana
  sd <- sd(x)         # Calcular o desvio padrão
  pearson <- 3 * (me - m) / sd  # Aplicar a fórmula do coeficiente de assimetria de Pearson
  return(pearson)     # Retornar o resultado
}

coef_assimetria_pearson_ibov = pearson(ibov)   
coef_assimetria_pearson_selic = pearson(selic) 


# Função para calcular o coeficiente de assimetria de Yule
yule = function(x) {
  q1 <- quantile(x, 0.25, type = 5)  # Primeiro quartil (Q1)
  q2 <- quantile(x, 0.5, type = 5)   # Mediana (Q2)
  q3 <- quantile(x, 0.75, type = 5)  # Terceiro quartil (Q3)
  
  # Cálculo do coeficiente de assimetria de Yule
  yule <- (q3 + q1 - 2 * q2) / (q3 - q1)
  names(yule) <- "yule"  # Atribui nome ao valor calculado
  
  return(yule)  # Retorna o resultado
}

coef_assimetria_yule_ibov = yule(ibov)   
coef_assimetria_yule_selic = yule(selic) 


# Função para calcular o coeficiente de assimetria de Kelley
kelley = function(x) {
  q1 <- quantile(x, 0.1, type = 5)  # Quantil de 10% (Q1)
  q2 <- quantile(x, 0.5, type = 5)  # Mediana (Q2)
  q3 <- quantile(x, 0.9, type = 5)  # Quantil de 90% (Q3)
  
  # Cálculo do coeficiente de assimetria de Kelley
  kelley <- (q3 + q1 - 2 * q2) / (q3 - q1)
  names(kelley) <- "kelley"  # Atribui nome ao valor calculado
  
  return(kelley)  # Retorna o resultado
}

coef_assimetria_kelley_ibov = kelley(ibov)   
coef_assimetria_kelley_selic = kelley(selic)

# Função para calcular o coeficiente percentílico de curtose
curt = function(x) {
  q10 <- quantile(x, 0.1, type = 5)  # Quantil de 10% (Q10)
  q25 <- quantile(x, 0.25, type = 5) # Quantil de 25% (Q25)
  q75 <- quantile(x, 0.75, type = 5) # Quantil de 75% (Q75)
  q90 <- quantile(x, 0.9, type = 5)  # Quantil de 90% (Q90)
  
  # Cálculo do coeficiente percentílico de curtose
  curt <- (q75 - q25) / (2 * (q90 - q10))
  names(curt) <- "curt"  # Atribui nome ao valor calculado
  
  return(curt)  # Retorna o resultado
}

# Exemplo de uso da função
coef_curtose_ibov = curt(ibov)  
coef_curtose_selic = curt(selic)


#escores Z
escores_z_bov = (ibov - media_bov) / desvio_bov
escores_z_selic = (selic - media_selic) / desvio_selic

#histograma 
# Se necessário, ajustando a escala da variável (dividindo por 100)
selic <- selic / 100

# Criando o histograma
histo_selic <- hist(selic, 
                    main="Histograma da Taxa Selic",  # Título do gráfico
                    xlab="Taxa Selic (%)",            # Rótulo do eixo X
                    ylab="Frequência",                # Rótulo do eixo Y
                    col="lightblue",                  # Cor das barras
                    border="black",                   # Cor da borda das barras
                    breaks=10,                        # Número de intervalos
                    xaxt="n")                          # Desativar o eixo X original

# Personalizando o eixo X para não ficar tão estranho
axis(1, at = seq(0, max(selic), by = 0.5), labels = seq(0, max(selic), by = 0.5))



histo_ibov = hist(ibov, 
     main="Histograma do ibovespa",    # Título do gráfico
     xlab="pontos ibov",              # Rótulo do eixo X
     ylab="Frequência",                  # Rótulo do eixo Y
     col="lightblue",                    # Cor das barras
     border="black",                     # Cor da borda das barras
     breaks=5)
#boxplot
box_ibov = boxplot(ibov, 
        main = "Boxplot do Índice Ibovespa", 
        xlab = "Índice Ibovespa", 
        ylab = "Valor", 
        col = "lightblue",       # Cor do boxplot
        ylim = c(min(ibov), max(ibov)),  # Limite do eixo Y
        border = "darkblue")    # Cor da borda do boxplot

# Boxplot para a taxa Selic
box_selic = boxplot(selic, 
        main = "Boxplot da Taxa Selic", 
        xlab = "Taxa Selic", 
        ylab = "Valor (%)", 
        col = "lightgreen",      # Cor do boxplot
        ylim = c(min(selic), max(selic)),  # Limite do eixo Y
        border = "darkgreen")   # Cor da borda do boxplot


selic_porcentagem <- selic * 100  

# Criando o boxplot ajustado
boxplot(selic_porcentagem, 
        main = "Boxplot da Taxa Selic", 
        xlab = "Taxa Selic", 
        ylab = "Valor (%)", 
        col = "lightgreen", 
        border = "darkgreen")



# Diagrama de dispersão
plot(selic, ibov, 
     main = "Diagrama de Dispersão: Taxa Selic x Ibovespa", 
     xlab = "Taxa Selic (%)", 
     ylab = "Ibovespa", 
     col = "blue", 
     pch = 19)

abline(lm(ibov ~ selic), col = "red", lwd = 2)

# Cálculo da correlação
correlacao <- cor(selic, ibov, method = "pearson")
cat("Correlação (Pearson):", correlacao, "\n")

# Interpretação da correlação
if (correlacao > 0) {
  cat("A correlação é positiva: à medida que a Taxa Selic aumenta, o Ibovespa tende a aumentar.\n")
} else if (correlacao < 0) {
  cat("A correlação é negativa: à medida que a Taxa Selic aumenta, o Ibovespa tende a diminuir.\n")
} else {
  cat("Não há correlação entre a Taxa Selic e o Ibovespa.\n")
}

