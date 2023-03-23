# Funzioni R
Indice:
- [Lettura dati da file](Formulario_funzionale.md#Lettura-dati-da-file)
- [Vettori e matrici](Formulario_funzionale.md#vettori-e-matrici)
- [Dataframe](Formulario_funzionale.md#Dataframe)
- [Grafici](Formulario_funzionale.md#Grafici)
- [Indici di posizione e di dispersione](Formulario_funzionale.md#Indici-di-posizione-e-di-dispersione)

## Lettura dati da file
```R
variable = read.table("file_name.txt", header=TRUE)
```

## Vettori e matrici
```R
v = c( 1, 2, 3, 3) #inizializzazione di un vettore
length(v) #restituisce la lunghezza del vettore v
M = matrix( data = c( 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 ), nrow = 4, ncol = 3, byrow = FALSE) #inizializzazione di una matrice
dim(M) #restituisce le dimensioni della matrice M
unique(v) #restituisce i valori univoci del vettore v
```

## Dataframe

### Inizializzazione di un dataframe
```R
esame = data.frame( matricola = as.character( c( 45020, 45679, 46789, 43126, 42345, 47568 ) ),
                    voti_S = c( 30, 19, 29, NA, 25, 26 ), 
                    voti_O = c( 3, 3, 1, NA, 3, 2 ), 
                    voti_TOT = c( 30, 22, 30, NA, 28, 28 ) )
```

### Informazioni di un DataFrame
```R
head(data_frame) # Restituisce le prime sei righe contenute nel dataframe
tail(data_frame) # Restituisce le ultime sei righe contenute nel dataframe
dim(data_frame) # Restituisce le dimensioni del dataframe
names(data_frame) # Resitituisce i nomi dei campi del dataframe
```

### Creazione di una variabile categorica
```R
data_frame$variable = as.factor( data_frame$variable )
```

### Crazione di una tabella di frequenza
```R
table( data_frame$variable ) #tabella delle frequenze assolute
table( data_frame$variable ) / sum( table( data_frame$variable ) ) #tabella delle frequenze realtive
```

## Grafici
```R
x11()
windows()
#Entrambi i comandi aprono una nuova finestra grafica su Windows
```

### Grafici di dispersione
Un <b>grafico di dispersione</b> è spesso usato quando si hanno due variabili, di cui una rappresenta un parametro di controllo (posto convenzionalmente sull'asse orizzontale) e l'altra la variabile misurata (posta convenzionalmente sull'asse verticale). Può risultare utile per visualizzare il grado di <b>correlazione tra la variabile misurata e il parametro di controllo</b>.
```R
plot(data_frame$variable_x, data_frame$variable_y, xlab = 'x_label', ylab = 'y_label', main = 'title')
points(data_frame$variable_x, data_frame$variable_y, col='colour', pch = 19) #points serve per creare dei pallini colorati, pch indica la forma (19=cerchio)
```

### Grafici a barre
I <b>grafici a barre</b> sono utili per visualizzare le <b>frequenze assolute e relative</b> di <b>variabili discrete</b>.
```R
barplot(variable_frequency, col=c('col_1', 'col_2'), ylab='y_label')
```

### Grafici a torta
I <b>grafici a torta</b> sono utili per visualizzare le <b>frequenze relative</b> di <b>variabili discrete</b>.
```R
pie ( table( data_frame$variable ) / sum( table( data_frame$variable ) ), main = 'title' )
```

### Istogrammi
Gli <b>istogrammi</b> contano la <b>frequenza dei dati in ogni intervallo di dati prefissato</b> di <b>variabili continue</b>.
```R
hist(data_frame$variable, xlab='x_label', main='title') # in ordinata ci sono le frequenze assolute
abline(v=median(data_frame$variable), col='red') # Crea una retta verticale in corrispondenza della mediana
abline(v=mean(data_frame$variable), col='green') # Crea una retta verticale in corrispondenza della media
```

### Diagrammi a candela
I <b>diagrammi a candela</b> sono utili per identificare eventuali <b>asimmetrie della distribuzione</b> e/o la presenza di valori estremi (<b>outliers</b>).</br>
Un diagramma a candela visualizza un rettangolo le cui basi inferiore e superiore visualizzano rispettivamente il primo e il terzo quartile. All'interno del rettangolo viene tracciata una linea in corrispondenza della mediana. Il limite inferiore è dato da `Q1 - 1.5*IQR`, mentre il limite superiore è dato da `Q3 + 1.5*IQR`. I cerchi sotto il limite inferiore e sopra il limite superiore rappresentano gli outliers.
```R
boxplot(data_frame$variable, ylab="y_label", main='title')
```

### Q-Q plot

### Scatterplot

## Indici di posizione e di dispersione

### Media (valore atteso)
```R
mean(vector)
```

### Varianza
```R
var(vector)
```

### Deviazione standard
```R
sd(vector)
```

### Massimo e minimo
```R
range(vector) #Restituisce sia il massimo che il minimo
max(vector)
min(vector)
```

### Mediana
```R
median(vector)
```

### Moda
```R
t_freq = table(vector)
t_freq
freq_of_most_common_value = max( t_freq )
freq_of_most_common_value
moda = t_freq[t_freq==freq_of_most_common_value ]
```

### Quantili
```R
quantile(vector, probs = 0.25) #In probs va indicato l'ordine del quartile
```

### Range interquartile
Il range interquartile è la differenza tra il primo e il terzo quartile.
```R
IQR(vector)
```

### Indici per un sottocampione
```R
tapply( data_frame$variable_1, data_frame$variable_2, mean )
tapply( data_frame$variable_1, data_frame$variable_2, var )
tapply( data_frame$variable_1, data_frame$variable_2, sd )
tapply( data_frame$variable_1, data_frame$variable_2, max )
tapply( data_frame$variable_1, data_frame$variable_2, min )
tapply( data_frame$variable_1, data_frame$variable_2, median )
tapply( data_frame$variable_1, data_frame$variable_2, quantile, probs=0.25 )
```

## Covarianza e indice di correlazione

### Covarianza

### Indice di correlazione

## Test di Shapiro
