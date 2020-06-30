# Tarea 3 
# Variables aleatorias multiples
## Kaseng Fong 
## B42609



# Parte 1. Mejor curva de ajuste para las funciones de densidades marginales X y Y.

Para obtener la mejor curva de ajuste para las funciones de las densidades marginales, a partir de los datos, se extrae los vectores mediante np.linspace los valores de las filas de X y las columnas de Y. Se extraen la sumatoria de cada columna y fila para la densidad marginal de X y Y  utilizando np.sum(), con estos datos se obtienen las graficas reales de las densidades marginales de Fx y Fy que se encuentran en la parte 4  del archivo. Seguidamente se procede a realizar el ajuste, donde se observa que el comportamiento de las graficas reales obtenidas representan una curva gaussiana, por lo que se define una funcion para obtener los parametros de "sigma" y "mu" donde se obtienen los siguientes parametros:

|        | X       | Y       |
|--------|---------|---------|
| \sigma | 3.2994  |  6.0269 |
| \mu    | 9.90484 | 15.0794 |


``` python
xy = pd.read_csv("xy.csv",header = 0,index_col=0)

x = np.linspace(5,15,11)
y = np.linspace(5,25,21)

fy= np.sum(xy,axis=0)
fx= np.sum(xy,axis=1)

#Curva de mejor ajuste. 
def gaussiana(x,mu,sigma):
    return 1/(np.sqrt(2*np.pi*sigma**2))*np.exp(-(x-mu)**2/(2*sigma**2))

param_x,_=curve_fit(gaussiana,x,fx)
param_y,_=curve_fit(gaussiana,y,fy)

print(param_x)
print(param_y)
```

# Parte 2 

 !Ecuacion is $$y = x^2$$


# Parte 3  


### 1. Correlacion 


``` python
xyp = pd.read_csv("xyp.csv",header = 0)

#Correlacion
x_1 = xyp["x"] 
y_1 = xyp["y"] 
p_1 = xyp["p"]

correlation = 0 
for i in range(len(xyp)):
    correlation = correlation + x_1[i]*y_1[i]*p_1[i]; 
print( "La correlacion es :" ,correlation)


```


### 2. Covarianza

``` python

#Covarianza 
covariance = correlation - (param_x[0]*param_y[0])
print( "La covarianza es :" ,covariance)


```

### 3. Coeficiente de Covarianza

``` python

# Coeficiente de covarianza
ccv = covariance/ (param_x[1]*param_y[1])
print( "El coeficiente de covarianza es :" ,ccv)


```
$$y = x^2$$

# Parte 4

## Curvas de las funciones de densidades marginales obtenidas de la parte 1. 


1. Curva de densidad marginal x
![image de pmfx](fx.png)
1. Curva de densidad marginal y
![image de mpmfy](fy.png)
1. Curva de  mejor ajuste para la densidad marginal x
![image de gaussx](ajustex.png)
1. Curva de mejor ajuste para la densidad marginal y
![image de gaussy](ajustey.png)
1. Curva de densidad marginal conjunta
![image conjunta](3d.png)



![equtionm]\