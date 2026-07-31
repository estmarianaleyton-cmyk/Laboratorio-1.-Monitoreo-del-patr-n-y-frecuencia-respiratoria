# Laboratorio 1

**Universidad Militar Nueva Granada**

**Asignatura:** Instrumentación biomedica y biosensores

**Estudiantes:** Dubrasca Martínez, Mariana Leyton, Joshara Valentina Palacios

**Fecha:** 28 de julio del 2026

**Título de la práctica:** Monitoreo del patrón y frecuencia respiratoria

# **Introducción**


# **Objetivos**


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
