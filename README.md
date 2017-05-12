# practica-19
#Ejercicio 
#2 series de tiempo con tendencia (alza y la baja) minimo 15 datos
#cortar estas series en el 80% de susu datos
#Graficar los 4 metodos holt junto con los datos reales

install.packages("fpp")
require(fpp)


s1<-read.csv(file.choose())
ts1<-ts(s1, start=2000)
ts1
plot(ts1)

c<-ts1[1:16,]
tc<-ts(c, start=2000)
tc

#holt lineal simple
mod1<-holt(tc, alpha=.8, beta=.2, initial="simple", h=5)
mod1
plot(mod1)

#holt lineal exponencial
mod2<- holt(tc, alpha=.8, beta=.2, initial="simple", exponential=TRUE, h=5)
mod2
plot(mod2)

#Tendencia Aditiva amortiguado
mod3<- holt(tc, damped=TRUE)
mod3

#Tendencia multiplicativa amortiguado
mod4<- holt(tc, exponencial=T, damped=T)
mod4


x11()
plot(mod2, main= "Pronostico s1")
lines(mod2$mean, col="blue", type="p")
lines(mod1$mean, col="red", type"o")
lines(mod3$mean, col="green", type"o")
lines(mod4$mean, col="5")
legend("topleft", lty=1, col=c("blue","red", "green", "5", "6"),
       legend=c("simple", "exponencial", "aditivo", "multiplicativo", "reales"))

plot(crecp)
