# ML-DIAMONDS-PRICES BY ADRIAN MADRID

![Texto alternativo](./diamante.png)


**EN ESTE PROYECTO, HEMOS UTILIZADO DIFERENTES MODELOS DE REGRESIÓN PARA PREDECIR LOS PRECIOS DE CADA UNO DE LOS DIAMANTES ENCONTRADOS EN UN DATASET DE KAGGLE, CUYO OBJETIVO ERA TENER UN RMSE MINIMO DE 1000, Y DE AHÍ, IR AJUSTANDO NUESTRO MODELO PARA REDUCIR NUESTRO MARGEN DE ERROR HASTA EL MÁXIMO POSIBLE**


## MODELO DE REGRESION LINEAL

Dentro de la carpeta de regresion lineal, podemos ver un archivo de limpieza, donde aplicamos una serie de filtros para quedarnos con un dataset limpio para poder entrenar.
Para la limpieza:
-He importado el archivo **train.csv** descargado de kaggle 
-He borrado las columnas categoricas para no perjudicar el modelo de regresion lineal
-He renombrado algunas columnas para una mejor aclaración de los datos
-Encontré valores de 0 en tres columnas, y he predecido esos valores ayudandome de otras variables del data y he rellenado los huecos
mediante una función llamada insertar_valor.
-He creado con seaborn un mapa de calor para ver la correlacion entre las variables y las que tuvieran una fuerte correlacion entre ellas las he eliminado, en este caso la columna de x,y y z. También elimine la columna de ids, obviamente no representaba relevancia.
-Finalmente, con mi data listo para entrenar, lo he exportado como un archivo csv llamado **modelo_regresionLineal.csv**

Para el modelo:
Basicamente he importado el modulo de sklearn LinearRegression para realizar mi modelo, y para ello he tenido que importar el archivo 
**modelo_regresionLineal.csv** que deje limpio para esta ocasion, y el archivo **predict.csv** sobre el que iba a hacer mis predicciones.
Tuve que nivelar las dimensiones del data de predict.csv para poder hacer la prediccion porque sino me iba a dar un error.
Finalmente hecha la predicción, convertimos a archivo csv un dataframe creado que contiene los id de los diamantes y las predicciones que saqué. El archivo subido a kaggle de este modelo es **TEST1.csv**.


Validación del modelo:
Hay otro archivo **prueba rmse para la regresion lineal.ipynb** donde compruebo el RMSE de mi modelo, y donde separo los datos 
con mi X e y de entrenamiento, y con mi x e y de prueba, ajustandome a las dimensiones que se pedían para el proyecto. 
En está ocasión tuve un error de más de 5000 dolares, por lo que automáticamente descarte este modelo de regresion lineal.



## MODELO DE REGRESION RANDOM FOREST REGRESSION

Dentro de la carpeta RANDOM FOREST, estan los archivos que he usado para la utilización de este modelo de machine learning.

Para la limpieza:
-Importe un archivo csv llamado **train_limpio.csv**, que basicamente es un dataset que deje preparado para este modelo y donde realice
su limpieza en otro archivo a la misma altura de este csv, ejecutado en jupiter llamado **limpieza_train.ipynb**.
-Borré las columnas x,y y z que tenian una fuerte correlacion entre ellas y tambien con la columna de quilates, por lo que no me parecía apropiado dejarlas ya que iba a sobreestimar mucho mis predicciones. También borre la columna de ids que no servía de nada.
-Decidí quedarme esta vez con las variables categoricas y comprobé sus valores únicos para ver si tenía que cambiar alguno, o escribirlo de manera correcta, o para directamente descartar esa columna, ya que si tuviera muchos valores unicos no podría trabajar tan bien nuestro modelo de random forest, pero en este caso, teníamos pocos valores unicos, asique todo perfecto.
-Convertí a ordinales las columnas categóricas con la funcion dummies que pandas tiene incorporado.
-Por último exporte el dataframe a un archivo csv llamado **train_para_entrenar.csv**.

Para el modelo:
-Exporte los archivos **train_para_entrenar.csv** que deje listo para entrenar el modelo, y el archivo **predict.csv** con el que haría mis predicciones posteriores.
-Dividi los datos de nuevo solamente utilizando el data que limpié.
-Con la libreria de sklear importe RandomForestRegressor para entrenar mi modelo y le puse como parametros un random_state de 
5, y con un numero de arboles de 1000. En el proceso de entrenar el modelo apenas tardo mucho y obtuve unas predicciones asombrosas.
-Como con el modelo de regresión lineal, exporte en un archivo csv el dataframe con la columna de los ids y con otra que tenía las predicciones. El archivo se llama **prediccion_final** y es el archivo que subí a kaggle.

Para la validación:
La misma técnica que con el de regresión lineal, salvo por la diferencia de que esta vez, tenía un RMSE de menos de 550 dólares. Una buena cifra donde conseguía el objetivo principal que era no tener una diferencia de mas de 1000 dolares.

Hay otro archivo llamado ajuste modelo con GRID SEARCH CV, donde se ha hecho algo de tuning para mejorar y ajustar un poco más nuestro modelo. Conseguimos pasar de 550, a 546 dolares, y aunque no sea mucha la diferencia ya es algo...
Estas últimas predicciones se han exportado a un archivo csv llamado **ajuste_modelo.csv**, y que será la última subida a kaggle.










