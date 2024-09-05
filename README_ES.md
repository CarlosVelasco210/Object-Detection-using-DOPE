[English](README.md) | Spanish

# Deteccion de Objetos y estimacion de pose utilizando DOPE

En este repositorio de GitHub, presento un proyecto utilizando [DOPE (Deep Object Pose Estimation)](https://github.com/NVlabs/Deep_Object_Pose) creado por NVIDIA y utilizando un Kinect One para la detección de un objeto en el laboratorio de robótica de la Universidad Veracruzana. El objetivo es integrar esta detección en un robot colaborativo UR3 para la interacción humano-robot.

# Creacion del Modelo 3D

Para la creacion del modelo 3D, utilice un objeto MegaBlock disponible en el laboratorio. Este objeto es del tamaño adecuado para que la pinza del robot lo pueda manipular sin problemas.

<div>
  <img src='./models3D/realBlock.gif' width='400'>
</div>

Para ello utilice dos modelos 3D diferentes uno descargado en linea.

<div>
  <img src='./models3D/redBlock_online.gif' width='400'>
</div>

Y otro modelo creado por mí con texturas más realistas, utilizando el generador 3D Luma Genie. Capturando fotos o videos del objeto desde diferentes ángulos se puede construir un modelo 3D detallado. Posteriormente, utilicé herramientas de Blender para ajustar y perfeccionar el modelo, logrando un resultado muy cercano al objeto físico con texturas más realistas.

<div>
    <img src='./models3D/redBlock_texture.gif' width='400'>
</div>


# Creacion del Dataset
## Primer Entrenamiento

Para el primer entrenamiento, se creo un dataset de 122,000 imagenes del modelo 3D descargado en linea utilizando la libreria NVISII de NVIDIA para generar datos sinteticos. El entrenamiento se realizo con el codigo proporcionado por DOPE con 60 epocas con un tamaño de lote de 32.

<img src='./graph_results/dataset1.jpeg' width='400'>

### Resultados

Se evaluo el modelo utilizando 13 escenarios distintos con el MegaBlock en diferentes tamaños, se utilizo los dos modelos Megablocks para ver que tan preciso era detectando estos dos modelos 3D de diferentes texturas.

| Escenario | Valor Promedio        | Desviación Estándar    | Proporción de Detecciones  | AUC (Área Bajo la Curva)   |
|-----------|-----------------------|------------------------|----------------------------|----------------------------|
| 1         | 9.906870236548304     | 8.730089099172021      | 26/100                     | 0.20766666666666667        |
| 2         | 0                     | 0                      | 0/97                       | 0                          |
| 3         | 4.771360665213297     | 0.8868278656527507     | 62/98                      | 0.5700680272108845         |
| 4         | 0                     | 0                      | 0/56                       | 0                          |
| 5         | 6.436392145667369     | 0.5776193611652325     | 6/93                       | 0.05602150537634409        |
| 6         | 5.293908563697143     | 3.1369345456007554     | 63/95                      | 0.590719298245614          |
| 7         | 4.684177619601435     | 1.0287874131013346     | 59/96                      | 0.5550868055555556         |
| 8         | 4.625755644287643     | 0.5151881786961665     | 36/100                     | 0.32550000000000007        |
| 9         | 5.2688453378081785    | 2.9757212741715073     | 70/97                      | 0.6431271477663231         |
| 10        | 5.875605982198354     | 4.223917584430453      | 62/96                      | 0.5678819444444444         |
| 11        | 4.919218770038036     | 1.8306451578183642     | 61/95                      | 0.5767894736842105         |
| 12        | 6.936023622666627     | 3.092900978172489      | 18/50                      | 0.3088666666666667         |
| 13        | 7.887882671293061     | 5.648607756930215      | 15/50                      | 0.25156666666666666        |

<div style="margin-bottom: 20px;">
  <img src='./graph_results/Vprom_Destand1.jpeg' width='400' style="display: inline-block;">
  <img src='./graph_results/AUC1.jpeg' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 40px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate1.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate1.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate2.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate2.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate3.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate3.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate4.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate4.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate5.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate5.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate6.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate6.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate7.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate7.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate8.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate8.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate9.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate9.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate10.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate10.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate11.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate11.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate12.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate12.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate13.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict1/RedBlockEvaluate13.gif' width='400' style="display: inline-block;">
</div>

## Segundo Entrenamiento

En el segundo entrenamiento, se creo un dataset de 44,159 imagenes con el MegaBlock texturizado. Utilice el modelo resultante del primer entrenamiento para darle continuacion al entrenamiento, incorporando estas nuevas imagenes.

<img src='./graph_results/dataset2.jpeg' width='400'>

### Resultados

Se utilizo los mismo 13 escenarios del entrenamiento anterior para evaluar el modelo.

| Escenario | Valor Promedio        | Desviación Estándar    | Proporción de Detecciones  | AUC (Área Bajo la Curva)  |
|-----------|-----------------------|------------------------|----------------------------|---------------------------|
| 1         | 4.02547667734152      | 0.294854334004394      | 91/100                     | 0.83365                   |
| 2         | 4.377124507780992     | 0.43501046908819674    | 83/97                      | 0.7780584192439861        |
| 3         | 4.130707876763564     | 0.4020600413911343     | 75/98                      | 0.6995068027210882        |
| 4         | 4.6499566270695905    | 1.1398785953953645     | 18/56                      | 0.2905357142857144        |
| 5         | 0                     | 0                      | 0/93                       | 0                         |
| 6         | 8.144268537909856     | 7.508623363573066      | 26/95                      | 0.2282105263157895        |
| 7         | 5.769006510502794     | 4.948573048197892      | 76/96                      | 0.6977777777777777        |
| 8         | 6.320994475258116     | 5.935781714203715      | 45/100                     | 0.3916833333333333        |
| 9         | 6.177859527555418     | 4.102924083124736      | 66/97                      | 0.5941580756013746        |
| 10        | 4.187575275960723     | 3.0834220546541466     | 64/96                      | 0.6087152777777779        |
| 11        | 5.600144265583258     | 5.270232251595552      | 61/95                      | 0.5680877192982456        |
| 12        | 4.269599060253238     | 1.865569930913061      | 43/50                      | 0.7837                    |
| 13        | 7.277334876754938     | 4.532606123822793      | 19/50                      | 0.32343333333333335       |

<div style="margin-bottom: 20px;">
  <img src='./graph_results/Vprom_Destand2.jpeg' width='400' style="display: inline-block;">
  <img src='./graph_results/AUC2.jpeg' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 40px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate1.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate1.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate2.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate2.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate3.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate3.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate4.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate4.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate5.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate5.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate6.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate6.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate7.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate7.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate8.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate8.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate9.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate9.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate10.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate10.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate11.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate11.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate12.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate12.gif' width='400' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_groundTruth/RedBlockEvaluate13.gif' width='400' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate13.gif' width='400' style="display: inline-block;">
</div>

# Comparacion de los modelos.
Aunque el segundo modelo muestra una mejor deteccion en comparacion con el primero, aun presenta algunas limitaciones en precision.

<div>
  <div style="display: inline-block; text-align: center;">
    <p>Modelo 1</p>
    <img src='./redBlock_predict1/RedBlockEvaluate1.gif' width='300' style="display: inline-block;">
  </div>
  <div style="display: inline-block; text-align: center;">
    <p>Modelo 2</p>
    <img src='./redBlock_predict2/RedBlockEvaluate1.gif' width='300' style="display: inline-block;">
  </div>
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate2.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate2.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate3.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate3.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate4.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate4.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate5.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate5.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate6.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate6.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate7.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate7.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate8.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate8.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate9.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate9.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate10.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate10.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate11.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate11.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate12.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate12.gif' width='300' style="display: inline-block;">
</div>

<div style="margin-bottom: 20px;">
  <img src='./redBlock_predict1/RedBlockEvaluate13.gif' width='300' style="display: inline-block;">
  <img src='./redBlock_predict2/RedBlockEvaluate13.gif' width='300' style="display: inline-block;">
</div>

# Evaluaciones Extras

Se realizo una evaluacion adicional en un entorno real, colocando el MegaBlock en 12 posiciones diferentes, moviendolo desde un punto A a punto B, y midiendo la precision a distancias de 30 y 60 centimetros. Se genero una matriz de confusion para cada pose.

<div align="center">
  <h3>Objeto a 30 centímetros de distancia de la cámara.</h3>
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose1.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose1_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose2.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose2_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose3.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose3_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose4.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose4_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose5.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose5_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose6.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose6_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose7.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose7_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose8.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose8_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose9.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose9_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose10.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose10_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose11.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose11_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock1/pose12.gif' width='500' style="display: inline-block;">
  <img src='./realBlock1/Pose12_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center">
  <h3>Objeto a 60 centímetros de distancia de la cámara.</h3>
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose1.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose1_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose2.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose2_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose3.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose3_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose4.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose4_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose5.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose5_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose6.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose6_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose7.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose7_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose8.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose8_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose9.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose9_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose10.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose10_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose11.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose11_cor.png' width='375' style="display: inline-block;">
</div>

<div align="center" style="margin-bottom: 20px;">
  <img src='./realBlock2/pose12.gif' width='500' style="display: inline-block;">
  <img src='./realBlock2/Pose12_cor.png' width='375' style="display: inline-block;">
</div>

# Modificando DOPE

DOPE incluye un apartado para utilizar el modelo con ROS, pero este utiliza la estimacion de pose del objeto y lo visualiza en un entorno virtual, cuando se realiza una comparacion de la nube de puntos que proporciona el Kinect One se ve que este tiene una diferencia muy lejana donde esta ubicado el objeto, para tratar de solucionar esto, se modifico el codigo utilizando la imagen de profundidad proporcionada por el Kinect One para calcular la profundidad del objeto y tener una ubicacion mas precisa, este fue el resultado que se obtuvo.

<div>
  <div style="display: inline-block; text-align: center;">
    <p>Codigo sin modificar</p>
    <img src='./graph_results/sinModificar.jpeg' width='400' style="display: inline-block;">
  </div>
  <div style="display: inline-block; text-align: center;">
    <p>Codigo Modificado</p>
    <img src='./graph_results/Modificado.jpeg' width='400' style="display: inline-block;">
  </div>
</div>


# Modelos y Pesos

En este repositorio viene incluido el link para descargar los dos modelos CAD 3D del objeto que utilice en este entrenamiento, y los pesos resultantes del entrenamiento 1 y del entrenamiento 2 [aqui](https://www.dropbox.com/scl/fo/z30ti4oiv12qbn281dkuf/AEr40yvWAVrmIc_vCb0TDj0?rlkey=fd04rh7bbsy77robgp27h6cdy&st=sh39y3ep&dl=0)