# NYC Taxi Tip Classifier


## Clasificador de Propinas para Viajes en Taxi en NYC (2020)
Inspirado en la charla "Keeping up with Machine Learning in Production" de Shreya Shankar

Este proyecto muestra la construcción de un modelo de machine learning utilizando datos de viajes de los taxis amarillos de Nueva York para el año 2020, proporcionados por la NYC Taxi and Limousine Commission (TLC).

La idea es identificar aquellos viajes donde la propina dejada por el pasajero fue alta, es decir, mayor al 20% del costo del viaje.

Para ello, ajustamos un modelo de clasificación binaria RandomForest usando los datos de los viajes de enero de 2020. Probaremos el modelo resultante sobre los datos de los viajes de febrero de 2020 y compararemos el desempeño del modelo usando la métrica de f1-score.

Este proyecto está diseñado para ser ejecutado en Google Colab, al que podemos acceder de manera gratuita solo teniendo un usuario de Google (Gmail) y un navegador web. No es necesario instalar nada en el computador local.


## Descripción del Dataset

El diccionario de los datos puede encontrarse [acá](https://www1.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf):

| Field Name      | Description |
| ----------- | ----------- |
| VendorID      | Código indicando el proveedor del registro. 1= Creative Mobile Technologies, LLC; 2= VeriFone Inc.       |
| tpep_pickup_datetime   | Fecha y hora cuando se activó el taxímetro.        |
| tpep_dropoff_datetime   | Fecha y hora cuando se desactivó el taxímetro.        |
| Passenger_count   | Número de pasajeros en el vehículo. Este valor es ingresado por el conductor.      |
| Trip_distance   | Distancia del viaje en millas reportada por el taxímetro.      |
| PULocationID   | Zona de Taxi de TLC donde se activó el taxímetro.      |
| DOLocationID   | Zona de Taxi de TLC donde se desactivó el taxímetro.      |
| RateCodeID   | Código de tarifa final al final del viaje. 1= Tarifa estándar, 2=JFK, 3=Newark, 4=Nassau o Westchester, 5=Tarifa negociada, 6=Viaje en grupo     |
| Store_and_fwd_flag | Indica si el registro del viaje se almacenó en la memoria del vehículo antes de enviarse al proveedor debido a la falta de conexión al servidor. Y= viaje almacenado, N= no almacenado |
| Payment_type | Código numérico que indica cómo pagó el pasajero. 1= Tarjeta de crédito, 2= Efectivo, 3= Sin cargo, 4= Disputa, 5= Desconocido, 6= Viaje anulado |
| Fare_amount | Tarifa calculada por el taxímetro basada en el tiempo y la distancia. |
| Extra | Extras y recargos misceláneos. Actualmente incluye los cargos de \$0.50 y \$1 por hora punta y noche. |
| MTA_tax | Impuesto MTA de \$0.50 que se activa automáticamente según la tarifa del taxímetro. |
| Improvement_surcharge | Recargo de mejora de \$0.30 aplicado a los viajes al inicio. Comenzó a aplicarse en 2015. |
| Tip_amount | Monto de la propina – Este campo se llena automáticamente para las propinas con tarjeta de crédito. No se incluyen propinas en efectivo. |
| Tolls_amount | Monto total de todos los peajes pagados en el viaje. |
| Total_amount | Monto total cobrado a los pasajeros. No incluye propinas en efectivo. |


## Estructura del Proyecto

├── LICENSE
├── README.md
├── data/
│ ├── processed/
│ │ ├── *.parquet
│ ├── raw/
│ │ ├── *.parquet
├── models/
│ ├── random_forest.joblib
├── notebooks/
│ ├── 01_nyc_taxi_train.ipynb
│ ├── 02_nyc_taxi_test.ipynb
│ ├── 03_nyc_taxi_analysis.ipynb
├── requirements.txt
├── src/
│ ├── init.py
│ ├── config.py
│ ├── data/
│ │ ├── data_download.py
│ │ ├── data_preprocessing.py
│ ├── features/
│ ├── visualization/
│ │ ├── visual.py


## Dependencias

Para instalar las dependencias listadas en un archivo requirements.txt en tu entorno Python, debes usar el comando pip. Aquí están los pasos detallados para hacerlo:

Paso 1: Crear y Activar un Entorno Virtual (Opcional pero Recomendado)
Crear un Entorno Virtual:
Es una buena práctica crear un entorno virtual para tu proyecto para aislar las dependencias del proyecto de otras instalaciones de Python en tu sistema.

sh
Copiar código
python -m venv env
Activar el Entorno Virtual:

En Windows:
sh
Copiar código
.\env\Scripts\activate
En MacOS/Linux:
sh
Copiar código
source env/bin/activate
Paso 2: Instalar las Dependencias desde requirements.txt
Instalar Dependencias:
Usa pip para instalar todas las dependencias listadas en requirements.txt.

sh
Copiar código
pip install -r requirements.txt