# Proyecto4_DataLab

### Temas

- [Introducción](#introducción)
- [Herramientas](#herramientas)
- [Procesamiento](#procesamiento)
  - [Limpieza de datos ](#limpieza_de_datos)
  - [Análisis exploratorio](#análisis_exploratorio)
  - [Hipótesis](#hipótesis)
  - [Score de Riesgo](#score_de_riesgo)
  - [Regresión Logistica](#regresion_logistica)
- [Conclusiones](#Conclusiones)
- [Recomendaciones](#Recomendaciones)
- [Recursos](#Recursos)

## Introducción

Datalab, una empresa de consultoría innovadora que se especializa en el análisis de datos, con el objetivo de ofrecer soluciones analíticas avanzadas.

Datalab se ha establecido como un socio de confianza para una variedad de empresas en distintos sectores. Su modelo de consultoría único permite a sus analistas de datos seleccionar proyectos que se alineen con sus intereses y experiencia, optimizando así la aplicación de sus habilidades técnicas en los contextos donde pueden tener un mayor impacto

### Objetivo

 El objetivo de este análisis es entender las tendencias y patrones en las calificaciones y reseñas de productos disponibles en Amazon, con el fin de proporcionar insights que puedan ayudar a mejorar la estrategia de precios, descuentos y satisfacción del cliente. 

### **Herramientas**
  1. Google BigQuery
  2. Google Colab
  3. Google Looker Studio
  4. Visual Studio

## **Procesamiento**

### 1.1 Limpieza de datos 
### 1.2 Análisis exploratorio

1.- Aplicar medidas de tendencia central

 > 
 >![Captura de pantalla 2024-07-31 150452](https://github.com/user-attachments/assets/4b6fab1d-4148-4873-941f-af7b22c29cff)

2.- Visualizar la distribución 

 > 
 >![Captura de pantalla 2024-07-31 151810](https://github.com/user-attachments/assets/a21264ce-17bc-4ee5-aeec-ebe227ee2b2b)

Interpretaciones:

Gráfica Preferencia en usos de crédito:
 + La gráfica muestra que a medida que se incrementa el uso de líneas de crédito no aseguradas contra activos personales, el ratio de deuda tiende a aumentar. Sin embargo, hay una variabilidad significativa, especialmente en los niveles más altos de uso de crédito no asegurado.

 Gráfica de Uso de líneas de crédito no aseguradas:
 +  La gráfica muestra que los usuarios en sus 40s y principios de los 50s tienen los picos más altos en el uso de líneas de crédito no aseguradas. Después de los 50 años, el uso disminuye notablemente. Esto sugiere que las personas en la mediana edad son más propensas a utilizar líneas de crédito no aseguradas.

  Gráfica de Uso de líneas de crédito aseguradas por patrimonio:
   + La gráfica indica que el uso de líneas de crédito aseguradas por patrimonio aumenta progresivamente desde los 20 años, alcanzando su punto máximo en los usuarios de 50-60 años. Después de esta edad, el uso disminuye gradualmente. Esto sugiere que las personas en su edad media y mayores tienen un mayor uso de líneas de crédito aseguradas por patrimonio.
     
 Observaciones generales: Los picos en el uso de crédito no asegurado ocurren a una edad ligeramente menor que los picos en el uso de crédito asegurado. Y las líneas de crédito aseguradas por patrimonio tienden a ser utilizadas por un rango de edad más amplio y tienen un uso máximo más alto comparado con las líneas de crédito no aseguradas.
  
3.- Calcular cuartiles, deciles o percentiles de los grupos de malos pagadores.

Se analizan las variables que podrían ayudarnos a definir como es un cliente mal pagador.

   Age
 > 
 > ![Captura de pantalla 2024-07-31 152320](https://github.com/user-attachments/assets/453f1a3b-920b-4927-be67-36f095427df2)

   Last_salary_month
 > 
 >![Captura de pantalla 2024-07-31 152329](https://github.com/user-attachments/assets/6a286c0d-45ed-4ce9-a0cd-752e89e2035a)

   Number_dependents
 >  
 >![Captura de pantalla 2024-07-31 152413](https://github.com/user-attachments/assets/29c7c030-a007-4d7b-929e-afaf4e5ae5db)

   Debt_ratio
 > 
 >!![Captura de pantalla 2024-07-31 152438](https://github.com/user-attachments/assets/b88277d9-6c74-4066-b0b3-9f62e2dcc914)

   Using_lines_not_secured_personal_asset
 > 
 >![Captura de pantalla 2024-07-31 152507](https://github.com/user-attachments/assets/328f10be-8a85-4d59-8f29-bcf043de79c8)

  Delay_30-59-89
 > 
 >![Captura de pantalla 2024-07-31 152541](https://github.com/user-attachments/assets/921d8238-2b5b-4953-85fb-9a86857a6811)

4.- Calcular la correlación entre variables numéricas continuas.

 > 
 >![Captura de pantalla 2024-07-31 152634](https://github.com/user-attachments/assets/729a35a1-5ac7-46a1-a57a-5814364fd07e)


 Last_month_salary / age

  Interpretación: 
  Hay una correlación positiva muy baja entre la edad  y el salario del último mes. Esto indica que a medida que la edad aumenta, el salario del último mes tiende a aumentar ligeramente, aunque la relación es muy débil.

 Debt_ratio / age
  Interpretación: 
  Hay una correlación positiva extremadamente baja entre la edad y el ratio de deuda. Esto sugiere que la edad tiene muy poca influencia en el ratio de deuda de una persona.

 Debt_ratio / last_month_salary
  Interpretación:
   Hay una correlación negativa muy baja entre el ratio de deuda (debt_ratio) y el salario del último mes. Esto implica que, a medida que el ratio de deuda aumenta, el salario del último mes tiende a disminuir ligeramente, pero la relación es muy débil.

  Debt_ratio / Using_lines_not_secured_personal_asset
  Interpretación: 
  Hay una correlación positiva extremadamente baja entre el ratio de deuda y el uso de líneas de crédito no aseguradas. Esto indica que el uso de líneas de crédito no aseguradas tiende a aumentar ligeramente con el aumento del ratio de deuda, pero la relación es prácticamente insignificante.

5.- Calcular riesgo relativo

Se analizan las variables para determinar el número de veces que corre el riesgo de suceder el evento (malos pagadores):

  Age
 
 > 
 >![Captura de pantalla 2024-07-31 153706](https://github.com/user-attachments/assets/f3bfee0a-026f-4770-a92a-0be0baf02d72)

 Interpretación: 
 + Mayor riesgo relativo (20-51 años): Los usuarios en el rango de edad de 20 a 51 años tienen el mayor riesgo relativo, lo que sugiere que esta cohorte es más propensa a incumplir sus pagos.
 + Menor riesgo relativo (51-96 años): Los usuarios en el rango de edad de 52 a 96 años tienen el menor riesgo relativo, indicando que este grupo es el más confiable en términos de pago.
 + Tendencias de edad: Hay una tendencia general a que el riesgo relativo disminuya con la edad.

Last_salary_month

 > 
 >![Captura de pantalla 2024-07-31 153748](https://github.com/user-attachments/assets/63e646bd-0d7f-4b05-9d7d-66e6ff0a49c1)

  Interpretación: 
 + Mayor riesgo relativo: Los usuarios en el rango de salario más bajo tienen el mayor riesgo relativo, lo que sugiere que entre son 3.65 veces más propensos a incumplir sus pagos.
 + Menor riesgo relativo: Los usuarios en el rango de salarios más elevados tienen el menor riesgo relativo, indicando que este grupo es el más confiable en términos de pago pues solo tiene un 39% de   
posibilidades de incumplir en sus pagos.
 + Tendencias Hay una tendencia general a que el riesgo relativo disminuya conforme aumentan los ingresos mensuales del cliente.

Number_dependents

 > 
 >![Captura de pantalla 2024-07-31 153846](https://github.com/user-attachments/assets/ba0678f7-db8e-4045-b735-a81f7af93551)

 Interpretación: 
 + Mayor riesgo relativo: Los usuarios en el rango de dependientes medio (+1) tienen 5.68 veces más probabilidades de incumplir en sus pagos.
 + Menor riesgo relativo: Los usuarios de los cuartiles 1 y 2  indican que no hay riesgo de que ocurra el evento en estos cuartiles, posiblemente porque no hay dependientes en estos grupos.
 + Tendencias Hay una tendencia general a que el riesgo relativo aumente conforme los dependientes.
   
Debt_ratio

 > 
 >![Captura de pantalla 2024-07-31 153931](https://github.com/user-attachments/assets/05b0f95f-765e-4b0c-abfd-f762be96bb16)

 Interpretación: 
 + Mayor riesgo relativo: Los usuarios del  tercer cuartil presentan el mayor riesgo relativo (1.40) y la tasa de malos pagadores más alta (2.24%). Este cuartil muestra un punto crítico donde el riesgo de incumplimiento es significativamente mayor.
 + Menor riesgo relativo: Los usuarios del cuartil 1 tienen menor riesgo relativo (0.71) de ser malos pagadores, con una tasa de malos pagadores de 1.35%.
 + Tendencias: A medida que el debt_ratio aumenta, tanto la tasa de malos pagadores como el riesgo relativo tienden a aumentar hasta el tercer cuartil. El cuarto cuartil, aunque tiene los ratios de deuda más altos, muestra un riesgo relativo menor (1.09) que el tercer cuartil, lo que sugiere que algunos de los deudores con ratios extremadamente altos pueden tener factores mitigantes no reflejados solo en el debt_ratio.

Using_lines_not_secured_personal_asset

 > 
 >![Captura de pantalla 2024-07-31 154416](https://github.com/user-attachments/assets/0578e5de-456c-439d-8166-38c0a81abae4)

Interpretación: 
 + Mayor riesgo relativo: Los usuarios del cuartil 4 tienen el mayor riesgo relativo (41.08) y la tasa más alta de malos pagadores (0.06559). El máximo uso de líneas de crédito no aseguradas en este cuartil es extremadamente alto (22,000), lo que sugiere un riesgo significativamente mayor de incumplimiento asociado con altos niveles de endeudamiento no asegura
 + Menor riesgo relativo: Los usuarios de el cuartil 1 presentan el menor riesgo relativo (0.038) y una muy baja tasa de malos pagadores (0.00089). Es el cuartil con el uso mínimo de líneas de crédito no aseguradas, indicando que un bajo nivel de endeudamiento a través de líneas no aseguradas está asociado con un bajo riesgo de incumplimiento.
 + Tendencias: Estos hallazgos sugieren que un mayor uso de líneas de crédito no aseguradas está fuertemente correlacionado con un aumento en el riesgo de incumplimiento. Esto podría indicar que políticas más estrictas en la concesión de crédito no asegurado o una evaluación más detallada del riesgo crediticio podrían ser necesarias para los individuos en los cuartiles superiores de uso.
### 1.3 Hipótesis

## Score de Riesgo
## **Regresión Logística**


### **Conclusiones**

### **Recomendaciones*


## **Recursos**

### Presentación del Proyecto 
Accede a la presentación del proyecto haciendo clic [aquí](https://drive.google.com/file/d/1GdkslQ3pPk7i1k2rmBQY7mdTkbuySkSC/view?usp=sharing)