# Carregar os dados
dados = read.csv("ibovSelic.csv")
#só para ter as datas em variavel
date = dados[,1]

#dados das variaveis de fato
ibov = dados[,2]
selic = dados[,3]
install.packages("e1071")

library(e1071)
# Resumo estatístico
summary(dados)

# Variância
var(dados)

# Desvio padrão
sd(ibov)

# Assimetria
skewness(selic)

# Curtose
kurtosis(ibov)

ajuste<-lm(ibov~selic)
summary(ajuste)
anova(ajuste)

plot(ibov, selic)
abline(lm(ibov~selic))

fit<-fitted(ajuste)
fit


res<-residuals(ajuste)
res
summary(res)
var(res)
sd(res)
skewness(res)
kurtosis(res)
plot(res)
boxplot(res)
hist(res)
qqnorm(res)
plot(fit,res)
plot(y,res)
plot(x,res)


shapiro.test(res)
Box.test(res, lag = 2, type = "Ljung-Box")

install.packages("lmtest")
library(lmtest)
bptest(ibov~selic)


pred<-data.frame(x = 5) #valor médio
predict.lm(ajuste,pred,interval="confidence", level = 0.95)
#valor predito
predict.lm(ajuste,pred,interval="prediction", level = 0.95)
