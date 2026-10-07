# Impacto de los ciberataques en la fiabilidad de los sistemas industriales

## Integración del riesgo cibernético en AMFE y RCM: impacto operativo y económico

**Daniel Flores de Francisco**
Consultor de Sistemas Informáticos | ISDEFE

---

## Resumen

La convergencia IT/OT ha convertido los ciberataques en una causa de fallo que la ingeniería de fiabilidad ya no puede tratar como un riesgo ajeno. Este trabajo analiza cómo los ataques sobre sistemas SCADA, dispositivos IIoT y plataformas de monitorización afectan a la disponibilidad, al MTBF, al MTTR y al coste del ciclo de vida. El ciberataque se distingue del fallo convencional por cuatro rasgos —no aleatoriedad, causa común, ocultación y recuperación prolongada— y actúa sobre todo a través del tiempo de recuperación y de la anulación de las redundancias. Se propone una metodología para incorporarlo al AMFE y al RCM y se evalúa con un caso ilustrativo el retorno de las medidas de mitigación: las que acortan la recuperación son las que más reducen la pérdida esperada, y la inversión se justifica incluso con probabilidades de incidente bajas.

**Palabras clave:** fiabilidad, ciberseguridad industrial, OT, AMFE, RCM, disponibilidad, MTTR, coste del ciclo de vida.

## 1. Introducción

La ingeniería de fiabilidad se ha ocupado tradicionalmente de fallos de origen físico (desgaste, fatiga, corrosión), operativo o humano, modelados como fenómenos aleatorios a partir de datos históricos. La digitalización ha cambiado ese escenario: los sistemas de control están hoy conectados a las redes corporativas, a plataformas de análisis y mantenimiento predictivo en la nube y a los accesos remotos de fabricantes y mantenedores. Esa convergencia IT/OT aporta eficiencia, pero amplía la superficie de ataque e introduce una clase de fallos cuyo origen no es la degradación de un componente, sino la acción deliberada de un adversario.

Los datos confirman la tendencia. Dragos contabilizó en 2025 más de 3.300 organizaciones industriales afectadas por ransomware, 119 grupos activos (un 49 % más que en 2024) y más de dos tercios de las víctimas en el sector manufacturero [1]. El caso de Jaguar Land Rover (JLR) ilustra la escala de las consecuencias: un ciberataque detuvo su producción cerca de cinco semanas en septiembre de 2025, con 196 M£ de costes excepcionales en el trimestre [2] y un impacto estimado de 1.900 M£ en la economía británica [3].

Este trabajo analiza cómo afectan los ciberataques a la fiabilidad industrial y propone integrarlos en el AMFE y el RCM, con especial atención a su impacto operativo y económico.

## 2. El ciberataque como mecanismo de fallo

### 2.1. Rasgos diferenciales

Un ciberataque con efecto sobre el proceso es una causa de fallo funcional, pero con cuatro rasgos que invalidan hipótesis habituales en fiabilidad:

- **No es aleatorio.** Su frecuencia no depende del envejecimiento, sino de la exposición del activo y de la capacidad e intención del atacante; puede aumentar bruscamente al publicarse una vulnerabilidad, y el histórico de averías no la predice.
- **Actúa como causa común.** La redundancia presupone fallos independientes, pero un ataque que explota un software o unas credenciales compartidas alcanza a la vez a todos los canales: en el modelo de factor β, β tiende a 1. En el ataque NotPetya (2017), Maersk perdió prácticamente todos sus controladores de dominio y pudo reconstruir su red gracias a un único servidor que había quedado desconectado en Ghana por un corte eléctrico [4].
- **Puede permanecer oculto.** El atacante permanece en la red semanas antes de actuar —14 días de mediana según M-Trends 2026 [5]; 42 días de media en el ransomware que alcanza entornos OT [1]— y puede enmascarar los síntomas: Stuxnet mostraba valores normales a los operadores mientras dañaba cerca de un millar de centrifugadoras. Son, en terminología RCM, fallos ocultos.
- **La recuperación es larga.** Restablecer exige detectar, contener, investigar, reconstruir desde copias limpias y volver a poner en marcha: días o semanas, frente a las horas de una avería mecánica típica. Además, a menudo se para preventivamente aunque la OT esté intacta: Colonial Pipeline detuvo su oleoducto seis días por un ransomware en sus sistemas corporativos [6], y Asahi paró en 2025 la mayoría de sus 30 fábricas japonesas al quedar inutilizados sus sistemas de pedidos y expedición [7].

### 2.2. Vectores de ataque y modos de fallo inducidos

La Tabla 1 relaciona los principales vectores con el modo de fallo que inducen, según las categorías de impacto de MITRE ATT&CK for ICS [8] (pérdida o manipulación de la visión y del control, pérdida de protección).

**Tabla 1. Vectores de ataque, modos de fallo inducidos e indicadores afectados**

| Vector y mecanismo | Modo de fallo inducido | Indicador afectado | Caso de referencia |
|------------------------------|--------------------------|--------------|------------------------------|
| SCADA, HMI e historiadores: ransomware o *wiper* | Pérdida de visión y de control; parada de planta | Disponibilidad, MTTR | Norsk Hydro (2019): 22.000 equipos en 170 centros; operación manual [9] |
| PLC/RTU y protocolos sin autenticación: escritura de registros, cambio de lógica o *firmware* | Operación fuera de la envolvente de diseño; daño físico | MTBF, coste de reparación | Stuxnet (2010); FrostyGoop (2024): 600 edificios sin calefacción ~48 h [10] |
| SIS: manipulación de los controladores de seguridad | Pérdida de la protección (fallo oculto) o disparo espurio | Seguridad, disponibilidad | Triton (2017): parada de una planta petroquímica [11] |
| IIoT y plataformas de monitorización: pasarelas comprometidas, datos falsos | Pérdida de observabilidad; decisiones de mantenimiento erróneas | MTBF, coste de mantenimiento | KA-SAT (2022): 5.800 aerogeneradores sin telemetría ni control remoto [12] |
| IT de soporte a producción y terceros (MES, ERP, accesos remotos) | Parada por dependencia funcional, con la OT intacta | Disponibilidad | Toyota (2022): 14 plantas paradas por un ataque a un proveedor [13] |

## 3. Impacto sobre los indicadores de fiabilidad

### 3.1. Disponibilidad y MTTR

Si a la tasa de fallo física λf se suma una tasa de origen cibernético λc, la indisponibilidad puede aproximarse por:

U ≈ λf · MTTRf + λc · MTTRc

Como MTTRc es dos o tres órdenes de magnitud mayor que MTTRf, una λc muy pequeña puede dominar la indisponibilidad. Sea una línea con MTBF = 400 h y MTTR = 4 h: su indisponibilidad es del 1 %, unas 87 h al año. Un ciberincidente con frecuencia de 0,1 al año y una recuperación de 10 días (240 h) añade solo 24 h anuales en valor esperado, pero el año en que ocurre multiplica casi por cuatro las horas de parada (de 87 a 327 h) y reduce la disponibilidad del 99,0 % al 96,3 %. El valor medio oculta el riesgo: son sucesos de baja frecuencia y alta consecuencia, que exigen criterios basados en la consecuencia, como en seguridad funcional.

### 3.2. MTBF y calidad de los datos de fiabilidad

Un ataque puede reducir el MTBF degradando los equipos directamente (operación fuera de diseño, como en Stuxnet), provocando paradas bruscas para las que no están dimensionados —en el ataque a una acería alemana en 2014, un alto horno no pudo detenerse de forma controlada y sufrió daños masivos [14]— o manipulando los datos del mantenimiento predictivo para que la degradación real pase inadvertida. Además, si los fallos cibernéticos se registran en el GMAO como averías técnicas, contaminan los análisis estadísticos (p. ej., de Weibull) y llevan a estrategias de mantenimiento erróneas. Dragos señala la clasificación de incidentes como «solo IT» como una debilidad del sector [1]; se propone añadir la causa cibernética a la taxonomía de causas de fallo del GMAO, según la estructura de ISO 14224 [15].

### 3.3. Coste del ciclo de vida

El coste del ciclo de vida (IEC 60300-3-3 [16]) se ve afectado por cuatro vías: el coste de indisponibilidad, que debe incluir la pérdida esperada por incidentes; el coste de mantenimiento, con nuevas tareas (parches, monitorización, pruebas de restauración); la obsolescencia, pues los activos OT duran 15–25 años y su software pierde el soporte mucho antes; y el coste regulatorio: NIS2 prevé multas de hasta 10 M€ o el 2 % de la facturación mundial para las entidades esenciales [17], y el Reglamento (UE) 2023/1230 de máquinas, aplicable desde enero de 2027, exige que los sistemas de mando resistan intentos maliciosos de crear situaciones peligrosas [18]. Por ello conviene incorporar la ciberseguridad desde el diseño. La Tabla 2 confirma que la duración de la recuperación, más que el daño inicial, determina el coste.

**Tabla 2. Impacto operativo y económico de incidentes representativos**

| Incidente | Impacto operativo | Impacto económico |
|--------------------------|--------------------------------------------|------------------------------|
| Maersk – NotPetya (2017) | 4.000 servidores y 45.000 PC reinstalados en 10 días; operación manual | 250–300 M$ [4] |
| Norsk Hydro – LockerGoga (2019) | 22.000 equipos afectados; plantas en manual durante semanas | ≈ 800 MNOK [9] |
| Colonial Pipeline (2021) | Oleoducto de 8.850 km parado 6 días; desabastecimiento regional | Rescate de 4,4 M$ más el coste de la parada [6] |
| Jaguar Land Rover (2025) | Producción detenida ~5 semanas; cadena de suministro afectada | 196 M£ en el trimestre; 1.900 M£ para la economía británica [2, 3] |

## 4. Metodología propuesta

La metodología no crea un análisis paralelo: trata el ciberataque como una causa de fallo más en los análisis que ya realizan los equipos de fiabilidad. Se inspira en la ingeniería basada en consecuencias (CCE) del Idaho National Laboratory [19] y en IEC 62443-3-2 [20], y consta de cuatro pasos.

**Paso 1. Funciones y dependencias.** Se identifican las funciones del activo y todos los sistemas de los que dependen —incluidos los IT de soporte a producción, los accesos remotos y los proveedores— en un diagrama de bloques que muestre las dependencias en serie y las redundancias que comparten software o credenciales.

**Paso 2. Vulnerabilidades críticas.** Se evalúan la exposición (conectividad con IT o Internet), las vulnerabilidades conocidas —priorizando las explotadas activamente, como las del catálogo KEV de CISA—, las configuraciones débiles (credenciales por defecto, protocolos sin autenticación) y la obsolescencia. En los SIS, IEC 61511-1 ya exige esta evaluación [21].

**Paso 3. Ciber-AMFE.** Se añaden al AMFE (IEC 60812 [22]) los modos de fallo cibernéticos de la Tabla 1. La severidad (S) usa la escala habitual, porque las consecuencias son físicas y operativas. La ocurrencia, que no puede estimarse con históricos, se sustituye por un índice de explotabilidad (E): 9–10 para activos accesibles desde Internet o desde una red corporativa sin segmentar, o con vulnerabilidades explotadas activamente; 4–6 en zonas segmentadas; 1–2 sin conectividad lógica. La detección (D) mide la capacidad de identificar el ataque antes del fallo funcional: 1–2 con monitorización continua del tráfico industrial; 9–10 si el ataque solo se manifiesta con el fallo o puede enmascararse. Dada la incertidumbre de E, y en línea con la prioridad de acción del manual AIAG-VDA [23], todo modo con S ≥ 9 requiere acción sea cual sea su NPR. En el ejemplo de la Tabla 3 (refrigeración con dos bombas 2 × 100 % gobernadas por un PLC), los modos cibernéticos superan con holgura al convencional y, en un AMFE clásico, habrían sido invisibles.

**Tabla 3. Extracto de ciber-AMFE de un sistema de refrigeración (valores ilustrativos)**

| Modo de fallo (causa) | Efecto | S | O/E | D | NPR | Tarea propuesta |
|-------------------------|-----------------------|----|-----|----|------|---------------------------------|
| Desgaste del rodamiento de la bomba A | Arranca la reserva | 4 | 5 | 3 | 60 | Análisis de vibraciones |
| Ransomware en SCADA/HMI | Parada preventiva de planta | 8 | 7 | 4 | 224 | Segmentación; copias probadas; operación manual |
| Modificación de la lógica del PLC | Paran ambas bombas: la redundancia no protege | 9 | 5 | 8 | 360 | Verificación de integridad de la lógica; bloqueo físico de programación |
| Datos falsos en la plataforma de vibraciones | Degradación inadvertida; fallo no anticipado | 6 | 6 | 7 | 252 | Telemetría autenticada; contraste con variables de proceso |
| Inhibición del disparo del SIS | Fallo oculto: sin protección | 10 | 3 | 9 | 270 | Independencia SIS/control; búsqueda de fallos; protección mecánica |

**Paso 4. Ciber-RCM.** Las tareas se seleccionan con la lógica de decisión del RCM (SAE JA1011 [24]):

- **A condición: monitorización continua.** La secuencia de un ataque industrial —intrusión en IT, movimiento lateral, preparación y ejecución contra el sistema de control [25]— define un «intervalo P-F cibernético» entre los primeros indicios detectables y el fallo funcional. Como la inspección debe ser mucho más frecuente que ese intervalo, se requiere monitorización continua. Su valor está medido: las organizaciones con visibilidad completa de su red OT detectan y contienen el ransomware en 5 días de media, frente a 42 en el conjunto del sector [1].
- **Búsqueda de fallos: las protecciones.** Copias de seguridad, reglas de cortafuegos o el propio SIS son protecciones con fallo oculto, cuya indisponibilidad media depende del intervalo de prueba T: U ≈ T / (2 · MTBF) para T pequeño frente al MTBF. Si una copia falla silenciosamente con un MTBF de dos años, probar su restauración una vez al año la deja indisponible en torno al 20 % del tiempo; cada trimestre, el 6 %.
- **Programadas: actualizaciones.** Parches, *firmware* y rotación de credenciales se planifican en las paradas programadas, priorizados por riesgo.
- **Rediseño: arquitectura.** Si ninguna tarea reduce a un nivel tolerable un riesgo con consecuencias para la seguridad, el RCM obliga a rediseñar: segmentación, eliminación de la exposición, independencia del SIS o protecciones mecánicas no programables (válvulas de alivio, disparos mecánicos por sobrevelocidad), inmunes a un ciberataque.
- **El mantenimiento como vector.** Portátiles, soportes extraíbles y accesos remotos de fabricantes son vías de entrada: se propone extender el permiso de trabajo a las intervenciones lógicas (autorización previa, equipos verificados, sesiones remotas registradas).

## 5. Medidas de mitigación y resiliencia operativa

Las medidas se ordenan según el parámetro de fiabilidad sobre el que actúan, para priorizarlas como cualquier otra inversión en fiabilidad.

**Segmentación de redes industriales (reduce λc y la causa común).** Zonas y conductos según IEC 62443, una DMZ industrial entre IT y OT y, en los activos más críticos, pasarelas unidireccionales. Limitan la exposición y, sobre todo, la propagación: evitan que un incidente corporativo —el caso más frecuente— se convierta en una parada de planta y que un mismo ataque alcance a todos los equipos redundantes.

**Detección de anomalías en tiempo real (mejora D y aprovecha el intervalo P-F).** Monitorización pasiva con inspección de protocolos industriales, que aprende el comportamiento normal del proceso y alerta de comandos anómalos, junto con la verificación periódica de la integridad de lógica y *firmware*.

**Refuerzo de las políticas de acceso (reduce λc).** Autenticación multifactor, gestión de accesos privilegiados, mínimo privilegio, control de soportes extraíbles y acceso remoto de terceros por un punto único, con sesiones autorizadas, limitadas en el tiempo y grabadas. El ataque que paró Toyota entró en su proveedor a través de un equipo de conexión remota [13].

**Mejora de la respuesta ante incidentes (reduce MTTRc, el término dominante).** Planes específicos para OT ensayados por IT, operación, mantenimiento y ciberseguridad; copias desconectadas o inmutables con restauración probada; imágenes de referencia de PLC, HMI y servidores; repuestos preconfigurados; y operación manual entrenada. Norsk Hydro mantuvo parte de su producción en manual; Maersk dependió de un servidor desconectado por azar: la recuperación debe diseñarse, no confiarse a la suerte. Todo ello se gestiona como un programa de fiabilidad más, con indicadores propios: activos críticos con copia verificada, tiempo de restauración ensayado y cobertura de la monitorización.

## 6. Impacto económico y retorno de la gestión proactiva

La pérdida anual esperada es ALE = f · C, siendo f la frecuencia anual y C el coste por incidente (lucro cesante, recuperación, daños y penalizaciones). La rentabilidad de las medidas se mide con el retorno de la inversión en seguridad, ROSI = (ALE₀ − ALE₁ − Cm) / Cm, donde Cm es su coste anual [26].

Se analiza una planta de fabricación de tamaño medio que opera 8.400 h/año con un coste de parada no planificada de 25.000 €/h, valor prudente frente a los 36.000 $/h que Siemens estima para el gran consumo o los 2,3 M$/h de la automoción [27]. El escenario de referencia es un ransomware que alcanza la capa de supervisión y obliga a parar 10 días (240 h): 7,5 M€ por incidente (6,0 M€ de parada, 0,9 M€ de respuesta y reconstrucción y 0,6 M€ de rearranque y penalizaciones), con una frecuencia supuesta de 0,10/año. Las medidas del apartado 5 reducen la frecuencia a 0,04/año y la parada a 48 h (1,6 M€ por incidente) y cuestan 0,32 M€/año (0,7 M€ de inversión amortizada en cinco años y 0,18 M€/año de operación). Los valores son ilustrativos y deben sustituirse por los de cada instalación.

**Tabla 4. Pérdida anual esperada por escenario (caso ilustrativo)**

| Escenario | f (año⁻¹) | Parada por incidente (h) | Coste por incidente (M€) | ALE (M€/año) | Parada esperada (h/año) |
|----------------------------------|----------|--------------|--------------|-------------|---------------|
| Sin medidas | 0,10 | 240 | 7,5 | 0,75 | 24,0 |
| Solo prevención (segmentación y accesos) | 0,04 | 240 | 7,5 | 0,30 | 9,6 |
| Solo recuperación (detección, copias y respuesta) | 0,10 | 48 | 1,6 | 0,16 | 4,8 |
| Defensa completa | 0,04 | 48 | 1,6 | 0,06 | 1,9 |

Se extraen cuatro conclusiones. Primera, la defensa completa reduce la pérdida esperada en 0,69 M€/año con un coste de 0,32 M€/año: un ROSI del 114 % y la recuperación de la inversión en menos de año y medio. Segunda, las medidas de recuperación aportan más que las de prevención (0,59 frente a 0,45 M€/año): cada hora de MTTR evitada vale 25.000 €, y pasar de 240 a 48 h ahorra 4,8 M€ por incidente. Tercera, el resultado es robusto: con la misma reducción relativa de frecuencia, la inversión es rentable si la frecuencia de un incidente con parada supera 0,047/año (uno cada 21 años). Cuarta, la cola del riesgo: un solo incidente sin medidas cuesta 7,5 M€, más de 23 veces el coste anual de la protección, y consume casi el 3 % de la disponibilidad anual; en un ciclo de vida de 15 años, las medidas acumulan ≈ 4,8 M€, menos que un único incidente.

No se incluyen costes como la reputación, las sanciones o el efecto en la cadena de suministro, que pueden multiplicar el coste directo: en JLR, el impacto estimado en la economía británica casi decuplicó los costes excepcionales del trimestre [2, 3].

## 7. Conclusiones

El ciberataque debe tratarse como un modo de fallo más, con rasgos propios —no aleatoriedad, causa común, ocultación y recuperación larga— por los que su impacto llega sobre todo a través del MTTR y de la anulación de las redundancias, y el valor esperado subestima el riesgo. El AMFE y el RCM pueden incorporarlo sin cambios estructurales: explotabilidad en lugar de ocurrencia, intervalo P-F cibernético, búsqueda de fallos en las protecciones y rediseño cuando está en juego la seguridad. La gestión proactiva es rentable incluso con probabilidades bajas, y las medidas de recuperación ofrecen el mayor retorno.

Se recomienda: incluir la causa cibernética en la taxonomía de fallos del GMAO; incorporar los modos cibernéticos al AMFE y al RCM de los activos críticos; ensayar el tiempo de recuperación ante ciberincidentes como un indicador de fiabilidad más; crear equipos mixtos de mantenimiento, operación y ciberseguridad; e incluir la ciberseguridad en el coste del ciclo de vida desde el diseño, anticipándose a NIS2, al Reglamento de Máquinas y al Reglamento de Ciberresiliencia [28]. Como línea futura, se propone modelizar los estados de compromiso con cadenas de Markov o redes de Petri.

En una instalación digitalizada, no hay fiabilidad sin ciberseguridad.

## Referencias

[1] Dragos (2026). *OT/ICS Cybersecurity Year in Review 2026*.

[2] Jaguar Land Rover Automotive plc (2025). *Resultados del segundo trimestre del ejercicio 2025/26*.

[3] Cyber Monitoring Centre (2025). *Jaguar Land Rover Cyber Event – Statement*.

[4] Greenberg, A. (2018). «The Untold Story of NotPetya». *Wired*.

[5] Mandiant – Google Cloud (2026). *M-Trends 2026*.

[6] Blount, J. (2021). Comparecencia ante el Senado de EE. UU., 8 de junio de 2021.

[7] Asahi Group Holdings (2025). Comunicados sobre el incidente de ciberseguridad.

[8] MITRE (2025). *ATT&CK for ICS*.

[9] Norsk Hydro (2020). Comunicados sobre el ciberataque y *Annual Report 2019*.

[10] Dragos (2024). *FrostyGoop ICS Malware: Intelligence Brief*.

[11] Johnson, B. et al. (2017). *Attackers Deploy New ICS Attack Framework «TRITON»*. FireEye.

[12] Viasat (2022). *KA-SAT Network Cyber Attack Overview*.

[13] Toyota Motor Corporation y Kojima Industries (2022). Comunicados sobre el ciberincidente.

[14] BSI (2014). *Die Lage der IT-Sicherheit in Deutschland 2014*.

[15] ISO 14224:2016. *Collection and exchange of reliability and maintenance data for equipment*.

[16] IEC 60300-3-3:2017. *Dependability management – Life cycle costing*.

[17] Directiva (UE) 2022/2555 (NIS2).

[18] Reglamento (UE) 2023/1230 relativo a las máquinas.

[19] Bochman, A. A. y Freeman, S. (2021). *Countering Cyber Sabotage: Introducing CCE*. CRC Press.

[20] IEC 62443-3-2:2020. *Security risk assessment for system design*.

[21] IEC 61511-1:2016+A1:2017. *Functional safety – SIS for the process industry sector*.

[22] IEC 60812:2018. *Failure modes and effects analysis (FMEA and FMECA)*.

[23] AIAG y VDA (2019). *FMEA Handbook*.

[24] SAE JA1011:2009. *Evaluation Criteria for Reliability-Centered Maintenance (RCM) Processes*.

[25] Assante, M. J. y Lee, R. M. (2015). *The Industrial Control System Cyber Kill Chain*. SANS Institute.

[26] Sonnenreich, W., Albanese, J. y Stout, B. (2006). «Return On Security Investment (ROSI)». *J. Res. Pract. Inf. Technol.*, 38(1), 45–56.

[27] Siemens (2024). *The True Cost of Downtime 2024*.

[28] Reglamento (UE) 2024/2847 (Reglamento de Ciberresiliencia).
