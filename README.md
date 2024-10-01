
# CHURN RATE MODEL PREDICTION

Este proyecto tiene como objetivo predecir qué clientes de una empresa de telecomunicaciones tienen mayor probabilidad de abandonar el servicio (churn). Utilizando técnicas de análisis de datos y modelado predictivo, buscamos identificar patrones y factores clave que influyen en la decisión de los clientes de dejar de ser usuarios, con el fin de implementar estrategias que mejoren la retención. 


## Exploración de datos

El conjunto de datos utilizado contiene 7,000 registros con 50 columnas. Realizamos un proceso de limpieza de datos, eliminando las variables geográficas y algunas variables posteriores a los eventos de churn, que no aportaban valor para el análisis.

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
Estos hallazgos proporcionan insights clave para la toma de decisiones estratégicas en el negocio, permitiendo implementar acciones que mejoren la retención de clientes y optimicen la experiencia de servicio.

![Proporción de clientes Churn por método de pago](https://github.com/mcpoveda2/ProyectoFinalPython/blob/checkpoint_sharon/PAYMENT%20VS%20CHURN%20LABEL.png)


## Authors

- [@mcpoveda2](https://github.com/mcpoveda2)
- [@MaSoraya](https://github.com/MaSoraya)
- [@ajalca](https://github.com/ajalca)
- [@sharonxnoboa](https://github.com/sharonxnoboa)
- [@mary moran](https://github.com/mcpoveda2)


