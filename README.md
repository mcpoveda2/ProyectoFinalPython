
# CHURN RATE MODEL PREDICTION

![Inicio](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/0_churn.png)

Este proyecto tiene como objetivo predecir qué clientes de una empresa de telecomunicaciones tienen mayor probabilidad de abandonar el servicio (churn). Tomando en cuenta que por cada porcentaje de mejora en la variable Churn podría aumentar en millones las ganancias de  las empresas, como el caso de la empresa AT&T. Utilizando técnicas de análisis de datos y modelado predictivo, buscamos identificar patrones y factores clave que influyen en la decisión de los clientes de dejar de ser usuarios, con el fin de implementar estrategias que mejoren la retención.

![Porque](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/1_porque_churn.png)
![Empresas](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/2_enfrentado_otras_empresas.png)

## Exploración de datos

El conjunto de datos utilizado contiene 7,000 registros con 50 columnas. Corresponden a América del Norte. Realizamos un proceso de limpieza de datos, eliminando las variables geográficas y algunas variables posteriores a los eventos de churn, que no aportaban valor para el análisis.

Nuestra variable objetivo ("target") fue "Churn Label", la cual es de tipo booleano con valores "Yes" o "No", e indica si un cliente abandonará el servicio (churn).

![Datos](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/3_que_encontramos.png)

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

![Datos](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/4_que_encontramos.png)
![Datos](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/5_que_encontramos.png)
![Datos](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/6_que_encontramos.png)
![Datos](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/7_que_encontramos.png)


## Feature Engineering
Agrupamos las edades y el satisfaction score para crear nuevas variables categóricas.
El score del 1 al 5, lo convertimos en alto, medio y bajo. 

![Evolucion](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/8_como_evolucionamos.png)

## Empezando el modelo

Realizamos el data splitting y escalamos las variables para asegurar que todas estuvieran en la misma escala. Ya que observamos que nuestra variable objetivo presentaba un desbalance de clases, con un 73% de clientes que no hicieron churn frente a un 26% que sí lo hicieron.
Inicialmente, incluimos la variable "Satisfaction Label" para entrenar el modelo, pero luego identificamos un posible target leakage. Esta variable parecía estar demasiado correlacionada con el resultado, absorbiendo gran parte de la importancia de los demás features. 

![Categorizando Satisfaction Score](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/satisfaction%20label%20categorica.png)

Como resultado, el modelo mostraba un rendimiento aparentemente muy alto, con una precisión superior al 90%, lo que indicaba que los resultados podrían no ser realistas debido a este sesgo.

En este repositorio encontrarán ambas versiones. 

![Categorizando Satisfaction Score](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/9_modelos.png) 
El algoritmo que decidimos utilizar fue el de Regresión Logística, ya que nos daba las mejores métricas de precisión y recall, versus los otros algoritmos evaluados como KNN, decision tree y SVC. 

## Entrenamiento y resultados
Se ven los valores altos o bajos de las característica en la predicción del Churn, se ven las variables más influyentes que incluyen el tipo de contrato ("Contract_Month-to-Month") y los cargos mensuales ("Monthly Charge"); para cuando no se usó Satifaction Score. Mientras cuando se incluyó está variable lo que predominaba era lo que daba bienestar al cliente como el nivel de satisfacción("Satisfaction Level") y la seguridad en línea("Online Security")

![Entrenamiento](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/10_features.png)
![Entrenamiento](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/11_features.png)

También se ve la contribución directa de cada variable con la predicción para un caso individual.
Las barras rojas representan contribuciones positivas (mayor probabilidad de churn), mientras que las barras azules indican contribuciones negativas (menor probabilidad de churn).
Variables como "Monthly Charge" y "Contract_Month-to-Month" tienen el mayor impacto en la predicción del Churn, mientras que características como "Tenure in Months" o "Total Long Distance Charges" también juegan un papel relevante.

![Entrenamiento](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/12_explainability.png)
![Entrenamiento](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/13_explainability.png)

## Decisiones de negocio
![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/14_matriz.png)

Con base en los valores de la matriz de confusión:

Verdaderos negativos (TN): 595
Falsos positivos (FP): 181
Falsos negativos (FN): 48
Verdaderos positivos (TP): 232
![Matriz de confusion](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/matriz_regresion.png) 

1. Riesgo mensual debido al churn: Son los ingresos mensuales que se pierden cuando los clientes hacen churn. Es el impacto mensual en términos de churn.
2. Pérdida de gastos acumulados: Muestra el monto total de los cargos acumulados que se perderán debido al churn.
3. Monto total de reembolso: Los reembolsos totales que se han realizado a los clientes que han hecho churn.
4. Pérdida de ingresos adicionales: Pérdidas relacionadas con cargos adicionales por uso de datos de los clientes que han hecho churn.
5. Pérdida de los servicios de larga distancia: Pérdidas debido a los cargos de larga distancia de los clientes que hicieron churn.

![KPIs](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/KPIs.png)

## Estrategias
Estos hallazgos proporcionan insights clave para la toma de decisiones estratégicas en el negocio, permitiendo implementar acciones que mejoren la retención de clientes y optimicen la experiencia de servicio. En este caso el análisis de la variable Churn nos permite implementar en el negocio categorizar a los clientes de alto riesgo, para generar estrategias que hagan que no abandone el servicio, ya sea con seguimientos, encuestas y beneficios, entre otros.

![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/15_inspiran.png)
![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/16_impulsando.png)
![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/17_limites.png)

Así mismo se puede integrar en el CRM según la gestión de relaciones con clientes para actualizar automáticamente el puntaje de churn de cada cliente después de cada interacción o actualización de datos. De esta forma se ajustan las estrategias en función del retorno de la inversión (ROI).

![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/18_conclusiones_recomendaciones.png)
![Resultado](https://github.com/mcpoveda2/ProyectoFinalPython/blob/main/images/diapositivas/19_future.png)

## Authors

- [@mcpoveda2](https://github.com/mcpoveda2)
- [@MaSoraya](https://github.com/MaSoraya)
- [@ajalca](https://github.com/ajalca)
- [@sharonxnoboa](https://github.com/sharonxnoboa)
- [@mary moran](https://github.com/Mar5555555)
