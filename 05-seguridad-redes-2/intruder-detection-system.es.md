---
title: "Intrusion detection systems (IDS)"
subtitle: "Guía completa de Intrusion Detection Systems (IDS): Tipos, Funcionamiento y Mejores Prácticas para Seguridad en Redes"
tags: ["networks"]
authors: ["blindma1den", "lorenagubaira"]

---

**IDS** (*Intrusion Detection System*) el sistema de detección de intrusiones consiste en un conjunto de métodos y técnicas para revelar actividad sospechosa sobre un recurso o recursos informáticos. Es decir, eventos que sugieran un comportamiento anómalo, incorrecto o inapropiado sobre un sistema.

Un sistema de detección de intrusiones puede ser descrito como un proceso de detección y monitorización de eventos que suceden en una red. Este sistema escucha y analiza toda la información que circula por una red, permite ayudar a entender los ataques, estimar los daños causados y tratar de prevenir otros ataques. Para detectar intrusiones en un sistema, los IDS utilizan tres tipos de información: un histórico de eventos, la configuración actual del sistema y, finalmente, procesos activos del sistema o reglas.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image19.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image19.png)

## **¿En qué consiste un IDS y cómo funciona?**

Hemos de partir de la base que aunque tengamos el cortafuegos habilitado, por normal general, tendremos muchos puertos abiertos, como por ejemplo el 80 y el 443 para las aplicaciones web. Por lo que debemos tener un sistema adicional que nos ayude a controlar estas puertas abiertas. Por lo que para llevar un mayor control debemos de utilizar un sistema IDS, esto es, un sistema de detección de intrusos y también de vulnerabilidades. Existen los IDS activos y los pasivos. Con los primeros se genera entradas en el registro y se generan alertas. Con los segundos en cambio, además de realizar las mismas funciones que con el pasivo, también se generarían acciones, como bloquear direcciones IP o cerrar el acceso a puertos restringidos.

Además desde el punto de vista del programación (*software*) existen diferentes tipos de herramienta, los sistemas de detección de intrusos (HIDS), sistemas de detección de intrusos en red (IDPS), los sistemas de detección de intrusos basados en firmas (SIDS) y por último los sistemas de detección de intrusos basados en anomalías.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image20.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image20.png)

Los sistemas IDS utilizan tres métodos para detectar el tráfico. Estos son la detección de anomalías, el análisis de protocolos y el análisis de firmas.

- Con la detección de anomalías tenemos como objetivo detectar un comportamiento anormal. Ejemplo de ello sería un volumen de tráfico ICMP (el que usa ping) inusual y muy elevado, que nos indicaría que somos el blanco o el emisor de un ataque de DDoS (Denegación de servicio)
- Respecto al análisis de protocolos se busca un tráfico de aplicación que no cumple el estándar del protocolo habitual.
- Por último, el análisis de firmas permite identificar ataques o comportamientos perjudiciales ya publicados. Suele ser la técnica más eficaz y la que no está sujeta a errores, ya que sólo se generan ataques o intrusiones que ya han tenido éxito en otro lugar, por lo que, pueden ser fácilmente identificados.

Es importante que nuestro IDS actualice la información de forma habitual, para así tener actualizadas siempre sus técnicas de análisis así como de las bases de datos de firmas.

Existen una serie de organizaciones, asociaciones y empresas que nos permiten estar al corriente de las evoluciones en materia de técnicas de intrusión y ataques. Las principales son:

- Bugtraq: Es una lista de difusión dedicada a la publicación de vulnerabilidades, su uso y corrección. ( [https://www.securityfocus.com/](https://www.securityfocus.com/))
- CERT: *Computer Emergency Response Team*. Se trata de una organización que estudia las vulnerabilidades, investiga las evaluaciones en términos de redes y seguridad y ofrece servicios relacionados con la seguridad. ([Entrada de Wikipedia al respecto](https://es.wikipedia.org/wiki/Equipo_de_Respuesta_ante_Emergencias_Inform%C3%A1ticas))
- CIAC: Computer Incident Advisory Capability. Una organización de alerta e investigación gestionado por el departament de energía de Estados Unidos. ( [https://www.energy.gov/cio/about-our-services/integrated-joint-cybersecurity-coordination-center](https://www.energy.gov/cio/about-our-services/integrated-joint-cybersecurity-coordination-center))

**Tareas de un IDS**

Un IDS realiza dos tareas fundamentales:

- Prevención: se realiza por medio de herramientas que escuchan el tráfico en la red o en un ordenador, denominados sensores, e identifican los ataques aplicando reglas, reconocimiento de patrones o técnicas inteligentes.
- Reacción: trata de detectar patrones de intrusión en las trazas de los servicios de red o en el comportamiento del sistema.

Existen indicadores estadísticos de sensibilidad, especificidad y precisión que permiten comprobar la efectividad del IDS, se basan en los siguientes conceptos:

- Verdaderos positivos (TP): Intrusión existente y correctamente detectada.
- Falsos positivos (FP): Intrusión no existente e incorrectamente detectada.
- Falsos negativos (FN): Intrusión existente y no detectada.
- Verdaderos negativos (TN): Intrusión no existente y no detectada.

**Tipos de IDS**

Existen distintas clasificaciones de los IDS, según sea su enfoque, origen de datos, estructura y comportamiento

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image21.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image21.png)

## **En función del enfoque**

Se presentan dos grupos: Los sistemas de detección de usos indebidos, que comparan las firmas con la información recogida; y los de detección de anomalías, que usan técnicas estadísticas para distinguir el comportamiento usual del anormal.

**Detección de anomalías:** Es necesario definir cuál es el comportamiento normal de un sistema por medio de un aprendizaje de actividades, para clasificar los comportamientos que se desvíen de lo normal como sospechosos. Estos sistemas son propensos a dar falsos positivos, que son producidos cuando se dispara una alerta con actividad normal. Tienen la desventaja de que depende de la calidad del proceso de aprendizaje. Existen tres técnicas diferentes para realizar la detección de anomalías en un sistema:

- **Sistemas basados en conocimiento:** Representa el inicio en los IDS, y se basa en las violaciones de seguridad detectadas mediante el uso de reglas. Resultan más fiables y proporcionan mejores rendimientos frente a ataques conocidos, con el inconveniente de su baja capacidad para detectar nuevos ataques no incluidos en la base de datos de firmas.
- **Sistemas basados en métodos estadísticos**: Basado en perfiles de actividad que vienen definidos por el comportamiento del usuario, con respecto a ficheros, programas, registros, etc. Se realiza mediante el establecimiento de métricas y modelos estadísticos.
- **Sistemas basados en aprendizaje automático:** Son los más desarrollados para el modelado de comportamientos normales y buscan mejorar los resultados en cuanto a detección, reducción de falsos positivos y tiempo de computación. Una ventaja reside en recoger las características de un ataque y añadirlo a una base de datos como firmas nuevas, permitiendo actualizar la base de firmas en un breve lapso de tiempo.
- **Detección de usos incorrectos (detección por firma/regla):** Los sistemas de detección basados en uso indebido monitorizan las actividades que ocurren en un sistema y las compara con una base de datos de firmas de ataques. Cuando se encuentra una actividad que coincide con una de estas firmas, se genera una alarma. Presentan una facilidad de adaptación ya que basta con actualizar la base de datos, ya sea, escribiendo la nueva regla u obteniéndola de un tercero.
- **Sistemas Expertos:** Conocimiento codificado mediante reglas de implicación (condición-acción), si se cumplen todas las condiciones se aplica la acción o regla. Presenta la desventaja de que las reglas no son secuenciales, lo que dificulta aislar pasos de intrusiones en el tiempo.
- **Detección de firmas:** Realiza comparaciones entre los eventos que ocurren en el sistema y las firmas almacenadas en la base de datos en busca de similitudes.
- **Análisis de transacción de estados:** Los ataques se representan como una secuencia de transiciones (máquina de estados finitos). Cuando se alcanza un estado considerado como intrusión se lanza una alarma.
- **Híbridos:** Los IDS basados en firmas resultan más fiables y proporcionan mejores rendimientos frente a ataques conocidos, pero presentan una deficiencia ante nuevos ataques. Los IDS basados en anomalías presentan la capacidad de detectar ataques desconocidos, pero su rendimiento es inferior. Los sistemas híbridos serán una mezcla de ambos, y por lo tanto, pueden ajustarse para operar como ambos tipos de detectores, mejorando la funcionalidad, la detección de ataques y la mejora de rendimiento.

## **En función del origen de los datos**

Se encuentran tres tipos de IDS atendiendo a las fuentes de información que se utilicen:

**HIDS (*Host-based Intrusion Detection Systems*):** Los IDS basados en el host solo procesan información de las actividades de los usuarios y servicios en una máquina determinada. Permite monitorizar los datos generados por un usuario, mediante el uso de *syslog1*, e identificar amenazas e intrusiones a nivel de host. Una desventaja proviene del requerimiento de confianza en el sistema, que puede estar infectado anteriormente a la instalación, y lo hace vulnerable ante ataques directos.

**NIDS (*Network Intrusion Detection Systems*):** Los NIDS son instalados en un dispositivo en modo promiscuo, realizan una escucha pasiva sobre la red de forma que no interfieren en su uso, analizando el tráfico en tiempo real, pero por contra, resultan inútiles ante ataques locales. Los nuevos sistemas, basados en agentes inteligentes, permiten una detección de nuevos ataques usando el concepto de centinelas, que supervisan el sistema para recoger toda la información necesaria para la detección.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image22.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image22.png)

**IDS Híbridos:** Los sistemas híbridos recogen lo mejor de ambos tipos HIDS y NIDS. Permiten una detección local de los sistemas y un sensor en cada segmento de red se encarga de la vigilancia. De esta forma se cubren las necesidades HIDS con las del NIDS, permitiendo el aprovechamiento de las ventajas de ambas arquitecturas.

## **En función de su estructura**

Clasificación basada en las estrategias de control:

**Sistema de Detección de Intrusión Distribuido (DIDS):** Se basa en la instalación en un sistema distribuido, ubicando sensores repartidos por varios equipos de la red. Estos sensores se comunican con un nodo central donde se recibirá toda la información y donde se cruzan los datos, lo que nos permitirá detectar los ataques con fiabilidad y obtener una visión global mejorando la detección de incidentes.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image23.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image23.png)

**Sistema de Detección de Intrusión Centralizado:** Emplea sensores que transmiten información a un sistema central que realiza el control, permitiendo ahorrar en equipamientos.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image24.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image24.png)

**En función de su comportamiento**

Encontramos dos tipos de IDS según si realizan la prevención escuchando el tráfico o si se elabora una respuesta defensiva cuando se detecta un ataque.

**IDS Pasivo:** Sólo notifican al administrador de la red pero no actúan sobre el ataque. Únicamente procesan la información en busca de intrusiones, y una vez detectada se genera una alerta.

**IDS Activos:** Es un tipo de IDS denominado Sistema de Prevención de Intrusión (IPS). A diferencia de los IDS, esta tecnología no se limita a escuchar el tráfico de la red y a mandar alertas, sino que permite establecer reglas, como se lo hace en los cortafuegos, para detener las intrusiones.

Intrusion prevention systems (IPS)

Los IPS son dispositivos de hardware o software encargados de revisar el tráfico de red con el propósito de detectar y responder a posibles ataques o intrusiones. La respuesta consiste en descartar o modificar los paquetes procedentes del ataque de tal manera que se anule su propósito. Este comportamiento los clasifica como dispositivos proactivos debido a su reacción automática a situaciones anómalas.

Los IPS se asemejan el comportamiento de los cortafuegos, ambos toman decisiones sobre la aceptación de paquetes en un sistema. Sin embargo, los cortafuegos basan sus decisiones en los encabezados de paquetes entrantes, capas de red y de transporte, mientras que los IPS basan sus decisiones tanto en los encabezados como en el contenido de datos del paquete.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image25.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image25.png)

***Encabezado y contenido de paquetes dependiendo del protocolo.***

La tecnología IPS ofrece una visión más exhaustiva de las operaciones de la red proporcionando información sobre todo tipo de actividades maliciosas, malas conexiones, contenido inapropiado y otras funciones, con una mínima vigilancia. Las principales características de esta tecnología son:

- Capacidad de reacción automática ante incidentes.
- Aplicación de nuevos filtros conforme detecta ataques en progreso.
- Bloqueo automático frente a ataques efectuados en tiempo real.
- Disminución de falsas alarmas de ataques a la red.
- Protección de sistemas no parcheados.
- Optimización en el rendimiento del tráfico de la red.

**Los IPS como evolución de los IDS**

Mientras el IDS se limita a detectar y notificar la intrusión al administrador del sistema, y éste se encarga de recibir y responder las alertas; el IPS detecta la intrusión y la detiene de algún modo ya predefinido, comprobando ciertos comportamientos en la red previamente configurados como anómalos. Gracias a este hecho, el nivel de alertas de un IPS es considerablemente menor que el nivel de alertas producido por un IDS. La diferencia principal entre los IDS activos y los IPS es que estos últimos están en capacidad de inutilizar los paquetes involucrados en el ataque modificando su contenido.

Una desventaja de los IPS viene por parte de la reacción proactiva ante las intrusiones. Por una parte, se tiene una disminución en el tiempo de reacción ante un ataque, pero también puede provocar efectos inesperados e inconvenientes cuando éste reacciona ante un falso positivo (FP), lo que podría llevar a una denegación de servicio o incluso al aislamiento de la máquina. Por ello, el uso de IPS en sistemas de control industrial ha de ser bien estudiado o en su defecto utilizar un cortafuego que posea inspección profunda de paquetes para mayor seguridad en las comunicaciones. Las arquitecturas actuales centralizan el funcionamiento del IPS, lo que facilita su operación y administración, pero disminuye la escalabilidad del sistema y convierte al IPS en un punto crítico.

![Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image26.png](Introduccio%CC%81n%20a%20la%20seguridad%20en%20redes%20b1630986b9024ea68d1f35b789d008f7/image26.png)

***Ventajas de los IPS***

## **Tipos de IPS**

Básicamente, los diferentes tipos de IPS se distinguen por su ubicación.

- **IPS basados en host (HIPS):** Esta aplicación de prevención de intrusiones reside en la dirección IP específica de un solo equipo, permite prevenir posibles ataques en los host.
- **IPS basadas en red (NIPS):** Monitorizan la red en busca de tráfico sospechoso.
- **IPS basado en red Wireless (WIPS):** Monitorizan redes inalámbricas, al igual que hacen los NIPS con redes LAN.
- **IPS basado en Análisis de Comportamiento de Red (NBA):** Examina el tráfico de red para identificar amenazas que generan tráfico inusual, como ataques de DoS o malware.

### **IPS basado en red (NIPS) vs IPS basado en host (HIPS)**

Un HIPS puede manejar el tráfico cifrado y sin cifrar por igual, ya que puede analizar los datos después de que hayan sido descifrados en el host. Por otra parte, un NIPS no utiliza el procesador y la memoria del host, por lo que no impacta en el rendimiento de la máquina.

Un NIPS puede detectar eventos dispersos a través de la red y puede reaccionar fácilmente, mientras que con un HIPS se tardaría demasiado tiempo en informar a un motor central y posteriormente informar al resto de los equipos.

### **La evolución y las categorías de los IPS**

Es posible distinguir dos generaciones históricas de los IPS:

- Los IPS de primera generación, al detectar un ataque proveniente de una dirección IP determinada, descartaban todos los paquetes de esa dirección, estuvieran o no involucrados en el ataque.
- La evolución de los IPS se debe a la capacidad de descartar únicamente los paquetes relacionados con el ataque identificado, permitiendo el tráfico de otros paquetes provenientes de la IP del atacante, siempre y cuando no estuvieran relacionados con el ataque.

Se pueden distinguir cinco categorías de IPS dependiendo de su funcionamiento, sus capacidades y su ubicación en la arquitectura de la red.

- **IPS *inline***

Estos IPS suponen la evolución de los NIDS basados en firmas y hacen la función de un Bridge a nivel de capa dos, revisando todos los paquetes que circulan por la red en busca de firmas. En caso de detectar alguna anomalía automáticamente es almacenado en un log, o incluso puede permitir el paso de un paquete alterando su contenido para de esta manera frustrar un ataque, sin que el atacante se dé cuenta. Este proceso es realizado mediante *Scrubbing*5, que consiste en la detección de errores por medio de verificación *checksum* o por redundancia con copias de datos. Habitualmente son conocidos como IPS de red o NIPS.

- **Switches a nivel de la capa de Aplicación (nivel 7 del modelo OSI)**

Los switches trabajan de forma habitual en el nivel 2 (enlace) pero cada vez son más habituales también los switches a nivel 7 o aplicación debido a la alta demanda de ancho de banda. La tarea principal de estos switches es balancear la carga de las aplicaciones distribuidas entre varios servidores, tomando decisiones de enrutamiento o conmutación a partir del contenido de los datos de la capa de aplicación. Hasta este punto no hay diferencia con un balanceador de carga.

El funcionamiento como IPS es similar a un NIPS basado en firmas, sirviendo para bloquear ataques. La posición de estos equipos suele ser delante de los cortafuegos, de manera que protejan la red completa. Al ser similares a un NIPS, sólo pueden parar ataques que conocen, pero permiten bloquear ataques de tipo DoS o DDoS que el resto de IPS no pueden parar y sin afectar al resto de la red. Se pueden configurar de forma redundante, en modo levantamiento en caliente o como balanceador de carga (característica que los diferencia de cualquier otro IPS).

- **Cortafuegos/IDS de Aplicación**

Los cortafuegos/IDS de aplicación se instalan en cada host que se desea proteger, teniendo en cuenta las aplicaciones que corren en él, por lo que también son conocidos como HIPS. Para su correcto funcionamiento será necesario hacer una fase de entrenamiento, que consiste en el proceso de identificación de patrones normales de funcionamiento en el host. Por medio de este entrenamiento se crea un perfil de relaciones frecuentes entre las aplicaciones y los componentes del sistema, como: el sistema operativo, otras aplicaciones, la memoria y los usuarios.

Los HIPS se comportan de forma similar a los IDS basados en detección de anomalías a la hora de detectar las intrusiones, pero deben identificar todos los procesos exhaustivamente, puesto que de no ser así pueden bloquear una aplicación válida.

Debido a que se apoyan en la detección de comportamientos anómalos y no en la coincidencia de firmas, es posible prevenir intrusiones muy recientes para las cuales todavía no existe una definición de sus firmas específicas.

- **Switches Híbridos**

Los switches híbridos son una combinación entre los HIPS y los switches de nivel de aplicación. Son dispositivos hardware como los switches de nivel de aplicación pero usan políticas similares a las utilizadas por los HIPS.

Los switches híbridos se basan en el análisis de patrones de comportamiento. La fortaleza radica en el conocimiento detallado del tráfico que debe aceptar.

- **Aplicaciones engañosas**

Este tipo de tecnología analiza todo el tráfico de red y de cada dispositivo en particular para disponer de un conocimiento de cuál es el tráfico permitido y correcto, similar a como realiza los patrones un HIPS. En el modo de funcionamiento, cuando detecta un tráfico que no está permitido para la red (acceso a un puerto no permitido) o para un servidor concreto (acceso a un puerto SSH a un servidor que no lo tiene abierto), envía una respuesta marcada al atacante, de manera que el IPS puede detectar otro tráfico de esa misma fuente y bloquearlo.
