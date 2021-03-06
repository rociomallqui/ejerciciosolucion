# ejerciciosolucion
Resolución de ejercicios parte 1 y parte 2
---

---

## Parte 1

### 1. Calcula los valores númericos aproximados de:

#### a.

```{r}
(0.3*0.15)/((0.3*0.15)+(0.2*0.8)+(0.5*0.12)) 
```

#### b.

```{r}
((5^6)/factorial(6))*exp(5)
```

#### c.

```{r}
datos<- matrix(c(20,7))
datos*0.4^7*0.6^13
```

### 2.Realizar la siguiente suma

```{r}
sum(1:1000)
```

```{r}
2+sum(2:512)*2
```

### 3. El vector grupo representa el grupo al que pertenece una serie de alumnos

#### a.¿Cuántos elementos tiene?

```{r}
length(grupo)
#Hay 192 elementos 
##profesor al correr el knit me sale ese error pero en el R todo normal 
```
#### b.¿En qué posiciones del vector está la letra “A”?

```{r}
posi<-c()
for(x in 1:length(grupo)){
  if("A"==grupo[x]){
    posi<-c(posi,x)
  }
}
posi
# [1]   2   8  17  21  28  84 101 108 111 115 123 136 190 192
```

### 4. El vector nota representa la nota de un examen de los alumnos que están en los grupos del vector grupo.

#### a.¿Cuanto suman todas las notas?

```{r}
sum(nota)
```

#### b.¿Cual es la media aritmética de todas las notas?

```{r}
mean(nota)
```


#### c.¿En qué posiciones están las notas mayores de 7.0?

```{r}
which(nota>7)
```

#### d.Visualiza las notas ordenadas de mayor a menor

```{r}
y<-order(nota)
z<-c()
for(x in y){
  z<-c(nota[y])
}
rev(z)
```

#### e.¿En qué posición está la nota máxima?

```{r}
for(x in 1:length(nota)){
  if(max(nota)==nota[x]){
    print(x)
  }
}
```
### 5. A partir de los vectores grupo y nota definidos.

##### a.Suma las notas de los 10 primeros alumnos del vector

```{r}
df<-data.frame(grupo,nota)
sum(nota[1:10])
```
#### b.¿Cuántos alumnos hay del grupo C?

```{r}
alum<-df[df$grupo=="C",]
length(alum$grupo)
```

#### c.¿Cuántos alumnos han aprobado?

```{r}
length(nota[ nota >= 5 ])
```


#### d.¿Cuántos alumnos del grupo B han aprobado?

```{r}
alum_b<-df[df$grupo=="B"&df$nota>5,]
length(alum_b$grupo)
```

#### e.¿Qué porcentaje de alumnos del grupo C han aprobado?

```{r}
alum_c<-df[df$grupo=="C"&df$nota>5,]
porc<-df[df$grupo=="C",]
length(alum_c$grupo)/length(porc$grupo) * 100
```
#### f.¿De qué grupos son la máxima y mínima notas de toda la muestra?

##### Máxima nota
```{r}
df[df$nota==max(nota),]
```
##### Mínima nota

```{r}
df[df$nota==min(nota),]
```

#### g.Nota media de los alumnos de grupo A y B, juntos, considerando sólo a los que han aprobado.

```{r}
df[df$grupo==c("A","B"),]
apro<-df[df$grupo==c("A","B")&df$nota>5,]
mean(apro$nota)
```

### 6. Calcula el percentil 66 de las notas de todos los alumnos, y también de los alumnos del grupo C.

```{r}
per_todos<-quantile(df$nota,0.66)
per_todos
```
```{r}
per_grupoc<-quantile(porc$nota,0.66)
per_grupoc
```

### 7. Un alumno tiene una nota de 4.9. ¿Qué porcentaje, del total de alumnos, tiene una nota menor o igual que la suya? ¿Y qué porcentaje tiene una nota mayor o igual que la suya?

```{r}
p<-length(nota[nota<=4.9])
a<-length(nota)
p/a*100
```
```{r}
p<-length(nota[nota>=4.9])
a<-length(nota)
p/a*100
```
### 8. Realiza el gráfico de diagramas de caja de las notas de cada grupo, para poder comparar el nivel de cada uno de ellos.

```{r}
boxplot(nota ~ grupo, data = df)
```

###  9.Si la variable conc recoge la concentración de plomo (en ppm) en el aire de cierta zona durante un día completo

#### a.¿Cuál ha sido la concentración máxima?

```{r}
conc
max(conc)
```
#### b.¿En cuántos de los muestreos se ha superado la concentración de 40.0 ppm?

```{r}
length(conc[conc>40])
```

#### c.¿Cuál ha sido la concentración media del día?


```{r}
median(conc)
```

#### d.¿Cuáles fueron las 10 mediciones más bajas del día?

```{r}
sort(conc) [1:10]
```

#### e.Si la primera medida fue a las 00:00. ¿A qué hora del día se alcanzó la concentración máxima?


```{r}
data.frame(conc)
minutos <- seq(
      as.POSIXct("2020-01-01 00:00" , format ("%Y-%m-%d %H:%M")),
      as.POSIXct("2020-01-01 23:59" , format ("%Y-%m-%d %H:%M")),
      by = "5 min"
      )
length(conc)
length(minutos)
df <- data.frame(conc, minutos)
df %>%
   filter (conc == max (df$conc))
```

## Parte 2 

### 1. Graficar los puntos (1,1),(2,4),(3,6),(4,8),(5,25),(6,36),(7,49),(8,61),(9,81),(10,100) en un plano utilizando RStudio.



```{r}
x<-c(1,2,3,4,5,6,7,8,9,10)
y<-c(1,4,6,8,25,36,49,61,81,100)
plot(x,y)
```

### 2.Ingresar la matriz A en RStudio  

```{r}
mt<-c(1,2,3,4,2,4,6,8,3,6,9,12)
mtA<-matrix(mt,ncol = 3,nrow = 4)
mtA
```

### 3. Ingresar la matriz identidad de tamaño 

```{r}
3*diag(3)
```

### 4.Crea una función que cree una matriz nula ingresando las dimensiones

```{r}
mtx<-function(x,y){
  P<-matrix(0,nrow = x,ncol = y)
  return(P)
}
mtx(2,4)
```

### 5. Modificar la matriz diag(4), para que se parezca a la matriz B  

```{r}
mtB<-diag(4)
mtB[1,1]<-0
mtB[2,2]<-2
mtB[3,3]<-3
mtB[4,4]<-4
mtB
```

### 6. Obtener la matriz transpuesta de A (ejercicio 2)

```{r}
t(mtA)
```

### 7. Realizar las siguientes operaciones A+B, A-B , 3B y AB

```{r}
mtA+mtB #dimensiones no compatibles
mtA-mtB #dimensiones no compatibles
```

```{r}
3*mtB
```

```{r}
mtA%*%mtB #argumentos no compatibles
  
```


###  8. Crea una función para calcular p^6

```{r}
p6<-function(e){
  x<-c(1,-2,1,2,4,0,3,-2,1)
  y<-matrix(x,ncol = 3)
  z<-y^e
  return(z)
}
p6(6)
  
  
```

### 9.Resolver el sistema de ecuaciones


```{r}
x<- matrix(c(3,9,3,-1,-2,1,1,1,-2),3,3)
x
y <- c (-1,-9,-9)
y
s<- solve(t(x)%*%x)%*%t(x)%*%y
s
```

### 10. Utilizando la ayuda de R, investigue para qué sirven las funciones eigen() y det()

```{r}
?eigen
#Calcula autovalores y autovectores de matrices numéricas (dobles, enteras, lógicas) o complejas.
```

```{r}
?det
#Calcula el determinante de una matriz. El determinante es una función genérica que devuelve por separado el módulo del determinante, opcionalmente en la escala logarítmica, y el signo del determinante.
```

### 11. Considerando las matrices

```{r}
v1<-seq(1,10,1)
v2<-seq(1,10,1)*2
v3<-seq(1,10,1)*3
v4<-seq(1,10,1)*4
v5<-seq(1,10,1)*5
B<-cbind(v1,v2,v3,v4,v5)
B
A<-matrix(rep(c(0,1)), ncol = 5,nrow = 5)
rep(c(0,1,0),2)
A[4:5,]<-c(0,1,1,0,0,1,0,1,1,0)
A
A%*%B # No se puede multiplicar porque los argumentos no son compatibles 
```

### 12. Considere B

```{r}
x<-matrix(1,5,2)
x[2,2]<--2
x[3,2]<-0
x[5,2]<-2
x
y<-matrix(1,5,1)
y[1:2,1]<-0
y[5,1]<-3
y
beta<-t(x)%*%x
ec<-solve(beta)
t<-ec%*%t(x)
t%*%y
```

### 13.Corre el siguiente código para cargar los vectores year y co2 en memoria

```{r}
data("co2")
means= aggregate(co2, FUN=mean)
year = as.vector(time(means))
co2= as.vector(means)
co2
year
dco2<-c()
for(x in 1:length(year)){
  r<- co2[x+1]-co2[x]
    dco2<-c(dco2,r)
}
dco2
plot(year,dco2, type = "b",pch=4 )
```

### 14.Lee el archivo rainfall.csv como un data.frame
Calcula e imprime un vector con los nombres de las estaciones donde al menos uno de los meses tiene una precipitación superior a 180mm.

```{r}
read.csv("rainfall.csv")
rmarkdown::render("tarea 2 rocio mallqui.rmd", output_format = "html_document")
