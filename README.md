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
En primer lugar se seleccionó un sensor de fuerza FSR402 para detectar los cambios producidos por la expansión y contracción del tórax durante la respiración. Para ello el sensor se ubicó sobre la parte frontal del pecho y se sujetó utilizando una banda. Antes de iniciar la adquisición de datos se verificó que el sensor permaneciera fijo durante todo el procedimiento y que respondiera a los movimientos respiratorios.
Luego el sensor se conectó a un circuito de acondicionamiento de señal conformado por un amplificador operacional LM741 y una resistencia de 10 kΩ, los cuales permitierón convertir las variaciones de resistencia del sensor FSR402 en una señal de voltaje proporcional a los movimientos respiratorios. La salida del circuito se conectó a una tarjeta de adquisición de datos (DAQ), encargada de digitalizar la señal y enviarla al computador para su procesamiento en MATLAB.
FOTOOO
Una vez realizada la conexión física del sistema se configuró la DAQ en MATLAB para recibir la señal proveniente del sensor. Se desarrolló un programa que permitió visualizar la señal respiratoria en tiempo real y almacenarla durante un período de 30 segundos para su posterior análisis.
Antes de realizar las mediciones definitivas se llevaron a cabo varias pruebas para verificar el funcionamiento del sistema. Se comprobó que la DAQ reconociera correctamente el canal de adquisición y que MATLAB recibiera los datos sin interrupciones. Después se ajustó la posición del sensor y la tensión de la banda ya que durante las primeras pruebas la señal presentaba poca variación cuando el sensor quedaba demasiado suelto. Estos ajustes permitieron obtener una señal con mayor estabilidad y una mejor representación de los ciclos respiratorios.
Una vez verificado el montaje se realizaron dos adquisiciones. En la primera nuestra compañera permaneció en reposo respirando de manera natural durante 30 segundos. En la segunda nuestra compañera realizó una lectura en voz alta durante el mismo tiempo, con el propósito de evaluar los cambios que producía la verbalización sobre el patrón respiratorio.
Finalizadas las adquisiciones, se procesaron para identificar los ciclos de inhalación y exhalación y obtener la frecuencia respiratoria correspondiente a cada esenario. Finalmente se compararon los resultados obtenidos durante el reposo y durante la verbalización con el fin de analizar las diferencias en el comportamiento de la respiración.



# **Resultados**

# **Discusion**

# **Conclusiones**

# **Referencias**
- [1] K. A. Powers and A. S. Dhamoon, “Physiology, pulmonary, ventilation and perfusion,” StatPearls Publishing, 2023. Accessed: July 31, 2026. [Online]. Available: https://www.ncbi.nlm.nih.gov/books/NBK539907/
- [2] A. Sapra, A. Malik, and P. Bhandari, “Vital Sign Assessment,” StatPearls, Treasure Island (FL), May 2023. Accessed: July 31, 2026. [Online]. Available: https://www.ncbi.nlm.nih.gov/books/NBK553213/
- [3] M. A. Cretikos, R. Bellomo, K. Hillman, J. Chen, S. Finfer, and A. Flabouris, “Respiratory rate: the neglected vital sign,” Medical Journal of Australia, vol. 188, no. 11, pp. 657–659, June 2018, doi: 10.5694/j.1326-5377.2008.tb01825.x.
- [4] “FSR 402 Data Sheet Figure 1 -Force Curve Industry Segments Interlink Electronics -Sensor Technologies FSR 400 Series Round Force Sensing Resistor,” Accessed: July 31, 2026. [Online]. Available: https://cdn.sparkfun.com/assets/8/a/1/2/0/2010-10-26-DataSheet-FSR402-Layout2.pdf
- [5] A. Akbar Khatami, H. Mukhtar, and Dien Rahmawati, “Performance Comparison of Strain Sensors for Wearable Device in Respiratory Rate Monitoring,” Lecture notes in electrical engineering, pp. 723–734, Jan. 2021, doi: 10.1007/978-981-33-6926-9_63.
