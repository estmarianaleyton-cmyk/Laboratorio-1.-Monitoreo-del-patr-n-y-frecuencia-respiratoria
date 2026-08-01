# Laboratorio 1

**Universidad Militar Nueva Granada**

**Asignatura:** Instrumentación biomedica y biosensores

**Estudiantes:** Dubrasca Martínez, Mariana Leyton, Joshara Valentina Palacios

**Fecha:** 28 de julio del 2026

**Título de la práctica:** Monitoreo del patrón y frecuencia respiratoria

# **Introducción**

La respiración es un proceso fisiológico vital mediante el cual el organismo obtiene el oxígeno necesario para el metabolismo celular y elimina el dióxido de carbono producido. El intercambio de gases ocurre principalmente por difusión simple en los alvéolos, donde los gases deben atravesar el surfactante alveolar, el epitelio alveolar, la membrana basal y el endotelio capilar, en un proceso gobernado por la ley de difusión de Fick, que describe cómo la difusión de un gas a través de la membrana alveolar depende de estas capas [1]. El ciclo completo, desde la inhalación hasta la exhalación, constituye el ciclo respiratorio, cuya repetición por unidad de tiempo define la frecuencia respiratoria (RR).

A pesar de su relevancia, la frecuencia respiratoria es el signo vital que con mayor frecuencia se omite en la evaluación de pacientes hospitalizados, con tasas de documentación que en revisiones recientes han variado entre 0.8% y 81.5% [2]. Esta situación es preocupante considerando que existe evidencia sustancial de que una frecuencia respiratoria anormal es un predictor de eventos clínicos potencialmente graves como el para cardio pulmonar o la necesidad de ingreso a cuidados intensivos [3], lo que resalta la necesidad de contar con herramientas accesibles que faciliten su monitoreo continuo y confiable.

En este contexto, la presente práctica tiene como objetivo el desarrollo de un sistema de adquisición basado en un sensor resistivo sensible a la fuerza (FSR402), cuya resistencia varía en función de la presión aplicada sobre su superficie [4], permitiendo detectar los movimientos torácicos o abdominales asociados a la respiración. Este tipo de sensores ha sido utilizado previamente para el monitoreo continuo de la frecuencia respiratoria; por ejemplo, un estudio comparó el desempeño de un sensor flex y un FSR402 colocados en el abdomen mediante un cinturón, durante 6 horas de monitoreo cada 10 minutos [5], evidenciando su viabilidad para esta aplicación. A partir de la señal adquirida, se buscó evaluar el patrón y la frecuencia respiratoria de un sujeto sano en condiciones de reposo y durante la lectura.

# **Objetivos**
**Objetivo general:**
- Evaluar la influencia del habla o verbalización sobre el patrón respiratorio.

**Objetivos específicos:** 
- Reconocer las variables físicas principalmente involucradas en el proceso respiratorio.
- Desarrollar un sistema que extraiga el patrón respiratorio y la frecuencia respiratoria.
- Identificar tareas de verbalización a partir del patrón y/o la frecuencia respiratoria.
  
# **MetodologÍa**
En primer lugar, se seleccionó un sensor de fuerza FSR402 con el propósito de detectar las variaciones de presión ocasionadas por la expansión y contracción del tórax durante el proceso respiratorio. Para ello, el sensor se ubicó sobre la región anterior del tórax y se fijó mediante una banda, asegurando un contacto constante con la superficie corporal. Antes de iniciar la adquisición de datos, se verificó que el sensor permaneciera firmemente sujeto durante todo el procedimiento y que respondiera adecuadamente a los movimientos respiratorios.

Posteriormente, el sensor se integró a un circuito de acondicionamiento de señal conformado por un divisor de voltaje y seguidor de voltaje. El divisor de voltaje esta conformado por una resistencia de 10 kΩ, con el fin de convertir las variaciones de resistencia del sensor en una señal de voltaje proporcional a los movimientos respiratorios. Esta señal fue acondicionada mediante un amplificador operacional LM741 configurado como seguidor de voltaje, cuya función consistió en adaptar la impedancia de salida del sensor para facilitar su adquisición por la tarjeta sin modificar la amplitud de la señal.

<img width="869" height="488" alt="image" src="https://github.com/estmarianaleyton-cmyk/Laboratorio-1.-Monitoreo-del-patr-n-y-frecuencia-respiratoria/blob/main/Captura%20de%20pantalla%202026-08-01%20094820.png"/>

**Fig 1. Montaje del sensor de fuerza resistivo en configuración divisor de voltaje y seguidor de voltaje.**

Una vez realizadas las conexiones físicas del sistema, se configuró la tarjeta de adquisición en MATLAB, estableciendo una frecuencia de muestreo de 100 Hz y un tiempo de adquisición de 30 segundos. Asimismo, se desarrolló un programa que permitió configurar la adquisición de datos, visualizar la señal respiratoria durante el registro, almacenar las muestras obtenidas y realizar su posterior procesamiento.

Previo a las mediciones definitivas, se efectuaron diversas pruebas con el fin de verificar el correcto funcionamiento del sistema de adquisición. En esta etapa, se comprobó que la tarjeta DAQ reconociera adecuadamente el canal analógico de entrada y que MATLAB recibiera la información de forma continua, sin pérdidas ni interrupciones. Adicionalmente, se realizaron ajustes en la posición del sensor y en la tensión de la banda elástica, debido a que durante las primeras pruebas la señal presentaba una baja variación cuando el sensor no ejercía suficiente contacto con el tórax. Estos ajustes permitieron mejorar la estabilidad de la señal y obtener una representación más clara de los ciclos respiratorios.

Una vez validado el montaje experimental, se realizaron dos adquisiciones de la señal respiratoria. En la primera, el sujeto permaneció en estado de reposo, respirando de manera natural durante un período de 30 segundos. En la segunda adquisición, el mismo sujeto realizó la lectura continua de un texto durante el mismo intervalo de tiempo, con el propósito de evaluar las modificaciones del patrón respiratorio ocasionadas por la verbalización.

Finalmente, las señales adquiridas fueron procesadas en MATLAB. Inicialmente, se eliminó la componente de corriente continua (DC) y posteriormente se aplicó un filtro digital Butterworth pasa-banda con frecuencias de corte de 0.08 Hz y 1 Hz, con el fin de conservar únicamente la información correspondiente a la respiración y reducir el ruido presente en la señal. Posteriormente, se identificaron los ciclos respiratorios mediante un algoritmo de detección de picos y se estimó la frecuencia respiratoria a partir del número de respiraciones registradas. De manera complementaria, se realizó el análisis en el dominio de la frecuencia mediante la Transformada Rápida de Fourier (FFT) para determinar la frecuencia dominante de la señal.

# **Resultados**

## ***Estado en resposo***

La Figura 2 presenta la señal respiratoria adquirida del sujeto en condición de reposo. En la gráfica se observa la señal original registrada por el sensor FSR402 de color gris y la señal obtenida después del procesamiento digital de color rojo, el cual incluyó la eliminación de la componente continua y la aplicación de un filtro Butterworth pasa-banda entre 0.08 Hz y 1 Hz.
Se evidencia que el filtrado permitió reducir las variaciones de alta frecuencia y las oscilaciones no asociadas al proceso respiratorio, obteniéndose una señal más suave y periódica. Asimismo, se observa que los ciclos respiratorios presentan una amplitud relativamente constante durante la mayor parte del registro, lo que indica un patrón respiratorio estable mientras el sujeto permaneció en reposo.

<img width="869" height="488" alt="image" src="https://github.com/estmarianaleyton-cmyk/Laboratorio-1.-Monitoreo-del-patr-n-y-frecuencia-respiratoria/blob/main/Figura2.png"/>

**Fig 2. Señal respiracion original y filtrada en estado en reposo.**

La Figura 3 muestra la detección automática de los picos correspondientes a cada ciclo respiratorio sobre la señal filtrada. El algoritmo identificó seis respiraciones durante los 30 segundos de adquisición, lo que corresponde a una frecuencia respiratoria de 12 respiraciones por minuto, lo cual se encuentra en un rango normal para un adulto saludable.

<img width="869" height="488" alt="image" src="https://github.com/estmarianaleyton-cmyk/Laboratorio-1.-Monitoreo-del-patr-n-y-frecuencia-respiratoria/blob/main/Figura3.png"/>

**Fig 3. Detección de picos.**

La Figura 4 presenta el espectro de magnitud obtenido mediante la Transformada Rápida de Fourier (FFT). Se identificó un pico dominante en 0.20 Hz, correspondiente a la frecuencia respiratoria del sujeto. Al convertir este valor a respiraciones por minuto se obtuvo una frecuencia de 12 respiraciones/min, coincidiendo con el resultado obtenido mediante el conteo de respiraciones.

<img width="869" height="488" alt="image" src="https://github.com/estmarianaleyton-cmyk/Laboratorio-1.-Monitoreo-del-patr-n-y-frecuencia-respiratoria/blob/main/Figura4.png"/>

**Fig 4. Espectro de frecuencia (FFT).**

## ***Durante la verbalización***




# **Discusion**

# **Conclusiones**

# **Referencias**
- [1] K. A. Powers and A. S. Dhamoon, “Physiology, pulmonary, ventilation and perfusion,” StatPearls Publishing, 2023. Accessed: July 31, 2026. [Online]. Available: https://www.ncbi.nlm.nih.gov/books/NBK539907/
- [2] A. Sapra, A. Malik, and P. Bhandari, “Vital Sign Assessment,” StatPearls, Treasure Island (FL), May 2023. Accessed: July 31, 2026. [Online]. Available: https://www.ncbi.nlm.nih.gov/books/NBK553213/
- [3] M. A. Cretikos, R. Bellomo, K. Hillman, J. Chen, S. Finfer, and A. Flabouris, “Respiratory rate: the neglected vital sign,” Medical Journal of Australia, vol. 188, no. 11, pp. 657–659, June 2018, doi: 10.5694/j.1326-5377.2008.tb01825.x.
- [4] “FSR 402 Data Sheet Figure 1 -Force Curve Industry Segments Interlink Electronics -Sensor Technologies FSR 400 Series Round Force Sensing Resistor,” Accessed: July 31, 2026. [Online]. Available: https://cdn.sparkfun.com/assets/8/a/1/2/0/2010-10-26-DataSheet-FSR402-Layout2.pdf
- [5] A. Akbar Khatami, H. Mukhtar, and Dien Rahmawati, “Performance Comparison of Strain Sensors for Wearable Device in Respiratory Rate Monitoring,” Lecture notes in electrical engineering, pp. 723–734, Jan. 2021, doi: 10.1007/978-981-33-6926-9_63.
