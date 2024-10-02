
# CHURN RATE MODEL PREDICTION

Este proyecto tiene como objetivo predecir qué clientes de una empresa de telecomunicaciones tienen mayor probabilidad de abandonar el servicio (churn). Tomando en cuenta que por cada porcentaje de mejora en la variable Churn podría aumentar en millones las ganancias de  las empresas, como el caso de la empresa AT&T. Utilizando técnicas de análisis de datos y modelado predictivo, buscamos identificar patrones y factores clave que influyen en la decisión de los clientes de dejar de ser usuarios, con el fin de implementar estrategias que mejoren la retención. 


## Exploración de datos

El conjunto de datos utilizado contiene 7,000 registros con 50 columnas. Corresponden a América del Norte. Realizamos un proceso de limpieza de datos, eliminando las variables geográficas y algunas variables posteriores a los eventos de churn, que no aportaban valor para el análisis.

Nuestra variable objetivo ("target") fue "Churn Label", la cual es de tipo booleano con valores "Yes" o "No", e indica si un cliente abandonará el servicio (churn).

### Preprocesamiento de Datos
Durante el preprocesamiento:

- Llenamos los valores nulos encontrados.
- Excluimos datos irrelevantes o redundantes.
- Normalizamos y codificamos variables categóricas para su análisis.
- Posteriormente, realizamos un análisis comparativo entre diferentes características categóricas y la variable objetivo "Churn Label", observando la influencia de diversas variables en la decisión de los clientes de abandonar el servicio:

#### Método de pago: 
Los clientes que menos abandonan el servicio suelen pagar con tarjeta de crédito.
#### Tipo de internet: 
Los clientes con fibra óptica presentan la mayor tasa de churn.
#### Contrato: 
Los contratos a largo plazo (2 años) retienen mejor a los clientes, mientras que los contratos de mes a mes tienen una mayor proporción de churn.
#### Satisfacción del cliente: 
Los clientes con fibra óptica reportaron los niveles más bajos de satisfacción.
### Conclusiones
Estos hallazgos proporcionan insights clave para la toma de decisiones estratégicas en el negocio, permitiendo implementar acciones que mejoren la retención de clientes y optimicen la experiencia de servicio. En este caso el análisis de la variable Churn nos permite implementar en el negocio categorizar a los clientes de alto riesgo, para generar estrategias que hagan que no abandone el servicio, ya sea con seguimientos, encuestas y beneficios, entre otros. Así mismo se puede integrar en el CRM según la gestión de relaciones con clientes para actualizar automáticamente el puntaje de churn de cada cliente después de cada interacción o actualización de datos. De esta forma se ajustan las estrategias en función del retorno de la inversión (ROI).

![Proporción de clientes Churn por método de pago](https://github.com/mcpoveda2/ProyectoFinalPython/blob/checkpoint_sharon/PAYMENT%20VS%20CHURN%20LABEL.png)
![Proporción de clientes Churn por método de pago](https://github.com/mcpoveda2/ProyectoFinalPython/blob/checkpoint_sharon/churn%20contrato.png)
![Proporción de satisfacción vs tipo de internet](https://github.com/mcpoveda2/ProyectoFinalPython/blob/checkpoint_sharon/satisfaction%20vs%20internet%20type.png)

## Feature Engineering
Agrupamos las edades y el satisfaction score para crear nuevas variables categóricas.
El score del 1 al 5, lo convertimos en alto, medio y bajo. 

## Empezando el modelo

Realizamos el data splitting y escalamos las variables para asegurar que todas estuvieran en la misma escala. Ya que observamos que nuestra variable objetivo presentaba un desbalance de clases, con un 73% de clientes que no hicieron churn frente a un 26% que sí lo hicieron.
Inicialmente, incluimos la variable "Satisfaction Label" para entrenar el modelo, pero luego identificamos un posible target leakage. Esta variable parecía estar demasiado correlacionada con el resultado, absorbiendo gran parte de la importancia de los demás features. 

![Categorizando Satisfaction Score](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/satisfaction%20label%20categorica.png)

Como resultado, el modelo mostraba un rendimiento aparentemente muy alto, con una precisión superior al 90%, lo que indicaba que los resultados podrían no ser realistas debido a este sesgo.

En este repositorio encontrarán ambas versiones. 

![Categorizando Satisfaction Score](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/METRICAS.png) 
El algoritmo que decidimos utilizar fue el de Regresión Logística, ya que nos daba las mejores métricas de precisión y recall, versus los otros algoritmos evaluados como KNN, decision tree y SVC. 

## Authors

- [@mcpoveda2](https://github.com/mcpoveda2)
- [@MaSoraya](https://github.com/MaSoraya)
- [@ajalca](https://github.com/ajalca)
- [@sharonxnoboa](https://github.com/sharonxnoboa)
- [@mary moran](https://github.com/mcpoveda2)


