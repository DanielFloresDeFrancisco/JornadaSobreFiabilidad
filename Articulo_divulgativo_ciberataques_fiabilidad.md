*Fiabilidad y ciberseguridad industrial*

# La avería que llega por la red

## Impacto de los ciberataques en la fiabilidad de los sistemas industriales: cómo paran una planta, cuánto cuestan y qué puede hacer el mantenimiento para evitarlo

**Daniel Flores de Francisco**\
Consultor de Sistemas Informáticos, ISDEFE

**Durante décadas, el gran enemigo del mantenimiento ha sido el desgaste: la fatiga de un eje, la corrosión de una tubería, el rodamiento que se calienta. Hoy hay otro que no se ve, no hace ruido y puede parar una fábrica entera en minutos. Este artículo explica por qué un ciberataque es, en el fondo, una avería más —aunque muy distinta de las que conocemos—, cuánto cuesta realmente y cómo pueden hacerle frente los equipos de mantenimiento con herramientas que ya utilizan a diario.**

> **[IMAGEN DE APERTURA]** Sala de control industrial con operadores frente a las pantallas de supervisión.
> *Pie de foto:* Las salas de control son los ojos de la planta. Si un ataque las bloquea, la instalación se queda ciega.

## La pregunta que todos nos hicimos

El 28 de abril de 2025, cuando la península ibérica se quedó sin luz, muchos nos hicimos la misma pregunta antes de saber qué había pasado: ¿ha sido un ciberataque? No lo fue. El informe del Gobierno descartó esa hipótesis y atribuyó el apagón a un problema de sobretensiones en la red eléctrica. Pero que fuera lo primero que nos vino a la cabeza dice mucho de cómo ha cambiado nuestra percepción del riesgo.

Pocos meses después, sí hubo un ciberataque detrás de una gran parada industrial. A comienzos de septiembre de 2025, Jaguar Land Rover tuvo que detener sus fábricas en el Reino Unido durante cerca de cinco semanas. La compañía contabilizó 196 millones de libras en costes extraordinarios en un solo trimestre, el Gobierno británico avaló un préstamo de 1.500 millones de libras para sostener a su cadena de proveedores y la producción de coches del país cayó un 27 % ese mes. El Cyber Monitoring Centre británico estimó el impacto total en unos 1.900 millones de libras, más de 2.100 millones de euros: el ciberataque más caro de la historia del Reino Unido.

No es un caso aislado. Dragos, una de las empresas de referencia en ciberseguridad industrial, contabilizó en 2025 más de 3.300 organizaciones industriales afectadas por *ransomware* —el ataque que bloquea los ordenadores y pide un rescate por liberarlos—, y más de dos tercios eran fábricas.

## Un fallo que no aparece en el plan de mantenimiento

Nuestras plantas están más conectadas que nunca. Los autómatas que mueven bombas y válvulas, las pantallas de supervisión y los sensores del mantenimiento predictivo están unidos a la red de la empresa, a la nube y a los accesos remotos de fabricantes y mantenedores. Es la llamada convergencia entre la informática de oficina (IT) y la tecnología que controla las máquinas (OT). Aporta eficiencia, pero también abre puertas.

Para la ingeniería de fiabilidad es un cambio de fondo. Sus herramientas —el AMFE (Análisis de Modos y Efectos de Fallo), el RCM (Mantenimiento Centrado en la Fiabilidad), la disponibilidad o el tiempo medio entre averías— se diseñaron para fallos que ocurren por azar o por envejecimiento. Un ciberataque no es azar: detrás hay alguien que quiere que la máquina falle.

## Cuatro razones por las que no es una avería más

**1. No avisa con el desgaste.** Un rodamiento da señales: vibra, se calienta, hace ruido. Un ciberataque no depende de la edad del equipo, sino de lo expuesto que esté y de quién quiera atacarlo. Es como un robo en casa: el riesgo no depende de lo vieja que sea la cerradura, sino de si la puerta se queda abierta. Por eso el histórico de averías no sirve para predecirlo.

**2. Rompe a la vez lo que estaba duplicado.** La forma clásica de ganar fiabilidad es la redundancia: dos bombas en lugar de una, dos servidores en lugar de uno. Funciona porque es muy improbable que fallen los dos a la vez. Pero si comparten el mismo programa o las mismas contraseñas, el atacante los alcanza a la vez. En 2017, el ataque NotPetya inutilizó prácticamente todos los servidores que gestionaban la red de la naviera Maersk en el mundo. Pudo reconstruirla gracias a un único servidor en Ghana que se salvó por casualidad: un corte de luz lo tenía desconectado en ese momento.

**3. Puede estar escondido.** Un atacante puede pasar semanas dentro de una red antes de actuar: la mediana es de 14 días, según el informe M-Trends 2026 de Mandiant. Y puede disimular. El virus Stuxnet, descubierto en 2010, mostraba a los operadores lecturas normales mientras dañaba cerca de un millar de centrifugadoras de una planta iraní de enriquecimiento de uranio; las roturas parecían averías mecánicas corrientes. Es el ladrón que, además de entrar, manipula la cámara de seguridad.

**4. Tarda mucho en arreglarse.** Una avería mecánica típica se resuelve en horas. Tras un ciberataque hay que averiguar qué ha pasado, aislar los equipos, reinstalarlos desde copias fiables y volver a arrancar con garantías: días o semanas. Y a menudo la planta se para aunque las máquinas estén intactas. En 2021, Colonial Pipeline cerró seis días el mayor oleoducto de combustibles de Estados Unidos, de 8.850 kilómetros, por un ataque a su informática de oficina, y provocó desabastecimiento en la costa este. En 2025, la cervecera japonesa Asahi detuvo la mayoría de sus 30 fábricas porque el ataque inutilizó sus sistemas de pedidos y envíos; durante semanas gestionó los pedidos con papel, bolígrafo y fax.

> **«Una avería mecánica se mide en horas; un ciberataque, en días o semanas. Y el coste lo marca el reloj.»**

> **[FIGURA 1]** `figuras/figura1_duracion_paradas.png`
> *Pie:* Duración de la parada o de la reconstrucción en cuatro ciberataques reales, comparada con una avería mecánica típica.

## Las cinco puertas de entrada

- **El centro de control.** Los ordenadores y pantallas desde los que se vigila y maneja el proceso (los sistemas SCADA). Si un ataque los bloquea, la planta se queda ciega. Le ocurrió en 2019 a la productora de aluminio Norsk Hydro: 22.000 ordenadores afectados en 170 centros y plantas trabajando en manual durante semanas.
- **Los autómatas.** Los «cerebros» que encienden motores y abren válvulas. Si alguien cambia su programa, puede forzar las máquinas fuera de sus límites. En enero de 2024, un ataque a una empresa de calefacción de la ciudad ucraniana de Leópolis dejó a más de 600 edificios de viviendas sin calefacción durante casi dos días, con temperaturas bajo cero.
- **Los sistemas de seguridad.** La última barrera, la que para la planta si algo se descontrola. En 2017, el programa malicioso Triton intentó manipularlos en una planta petroquímica de Arabia Saudí; el intento acabó provocando la parada de la instalación.
- **Los sensores y plataformas de monitorización.** Los ojos del mantenimiento predictivo. Si se manipulan sus datos, mantenimiento decide a ciegas. En 2022, un ataque a una red de comunicaciones por satélite dejó a unos 5.800 aerogeneradores de Europa central sin supervisión ni control a distancia.
- **La informática de la empresa y los proveedores.** Las fábricas dependen de sistemas de pedidos, planificación y logística, y de sus proveedores. En 2022, Toyota paró sus 14 plantas en Japón durante un día —unos 13.000 vehículos sin fabricar— porque un proveedor de piezas sufrió un ataque.

> **[IMAGEN]** Autómata programable (PLC) en un armario eléctrico, con su llave de modo visible.
> *Pie de foto:* Muchos autómatas tienen una llave física que impide cambiar su programa. Dejarla en modo «programación» es como dejar las llaves puestas en la puerta.

## Lo que cuesta de verdad

El daño de un ciberataque industrial rara vez está en la máquina rota: está en las horas que la planta deja de producir. Según el estudio *The True Cost of Downtime 2024* de Siemens, una hora de parada no planificada cuesta de media 2,3 millones de dólares en una gran planta de automoción y unos 36.000 dólares en el sector de gran consumo. Los grandes ciberataques de los últimos años lo confirman:

| Caso | Qué se paró | Cuánto costó |
|---|---|---|
| Maersk (2017) | Su red informática mundial: 4.000 servidores y 45.000 ordenadores reinstalados en 10 días | Entre 250 y 300 millones de dólares |
| Norsk Hydro (2019) | 22.000 ordenadores; plantas en manual durante semanas | Unos 800 millones de coronas noruegas (más de 70 millones de euros) |
| Colonial Pipeline (2021) | El mayor oleoducto de combustibles de EE. UU., durante 6 días | 4,4 millones de dólares de rescate, además de la parada |
| Jaguar Land Rover (2025) | Sus fábricas británicas, durante unas 5 semanas | 196 millones de libras en un trimestre; unos 1.900 millones para la economía británica |

Hay, además, costes menos visibles:

- **Daños en los equipos.** Una parada brusca somete a las máquinas a esfuerzos para los que no están pensadas. En 2014, un ataque a una acería alemana impidió apagar de forma controlada un alto horno, que sufrió daños graves, según la agencia alemana de ciberseguridad (BSI).
- **Datos de mantenimiento contaminados.** Si una avería provocada se registra en el programa de gestión del mantenimiento (GMAO) como un fallo técnico normal, las estadísticas se equivocan y el plan de mantenimiento se construye sobre información falsa.
- **Sanciones y obligaciones.** La directiva europea NIS2 prevé multas de hasta 10 millones de euros o el 2 % de la facturación mundial en sectores esenciales, y el nuevo Reglamento europeo de máquinas, aplicable desde enero de 2027, exige que los sistemas de control resistan manipulaciones malintencionadas.
- **Máquinas que duran más que su software.** Una instalación puede funcionar 25 años, pero sus ordenadores dejan de recibir actualizaciones mucho antes. Si no se prevé al comprar, se paga después.

## El mantenimiento ya tiene las herramientas

La propuesta es sencilla: no crear un mundo aparte, sino tratar el ciberataque como una causa de fallo más dentro de los análisis que los equipos de fiabilidad ya hacen. Se resume en cuatro pasos.

**Paso 1. Saber de qué depende cada equipo.** No solo de la electricidad o del aire comprimido, también de qué ordenadores, redes, accesos remotos y proveedores. Aquí suele saltar la sorpresa: líneas que parecían independientes dependen del mismo servidor.

**Paso 2. Buscar los puntos débiles.** Equipos accesibles desde internet, contraseñas que nunca se cambiaron desde fábrica, ordenadores sin actualizar o sistemas tan antiguos que ya no tienen soporte.

**Paso 3. Incluir el ataque en el AMFE.** Pensemos en un sistema de refrigeración con dos bombas, una en reserva, gobernadas por un mismo autómata. El AMFE clásico analiza, por ejemplo, el desgaste de un rodamiento: si falla una bomba, arranca la otra y no pasa nada. Pero si alguien modifica el programa del autómata, las dos bombas se paran a la vez y la redundancia no sirve de nada. Ese fallo, el más grave de todos, no aparecía en el análisis tradicional. Un matiz importante: ante un fallo mecánico se pregunta «¿con qué frecuencia ocurre?»; ante un ataque, la pregunta útil es «¿qué fácil es provocarlo?». Y todo fallo de consecuencias muy graves debe tener respuesta, por improbable que parezca.

| Qué puede fallar | Qué ocurre | Gravedad | Qué hacer |
|---|---|---|---|
| Desgaste del rodamiento de una bomba | Arranca la bomba de reserva | Baja | Análisis de vibraciones |
| Bloqueo de las pantallas de control | Se para la planta por precaución | Alta | Separar redes, copias de seguridad probadas y saber operar en manual |
| Cambio malintencionado del programa del autómata | Se paran las dos bombas a la vez | Muy alta | Comprobar periódicamente que el programa no ha cambiado; llave del autómata en modo funcionamiento |
| Datos falsos en la plataforma de vibraciones | El desgaste real pasa inadvertido | Media | Proteger las comunicaciones de los sensores y contrastar con otras medidas |
| Anulación del sistema de seguridad | La planta pierde su última protección | Muy alta | Sistema de seguridad independiente, pruebas periódicas y protecciones mecánicas |

*Ejemplo simplificado de AMFE ampliado con fallos de origen cibernético.*

**Paso 4. Elegir las tareas como en el RCM.** Muchas ideas del mantenimiento de siempre se trasladan casi literalmente:

- **Vigilar el estado, como con las vibraciones.** Un ataque no ocurre en un instante: el atacante entra, se mueve por la red, estudia el proceso y solo después actúa. Entre la entrada y el daño hay una ventana, igual que entre los primeros síntomas de un rodamiento y su rotura (el intervalo P-F). Aprovecharla exige vigilar la red de forma continua: según Dragos, las empresas que lo hacen detectan y contienen un *ransomware* en 5 días de media, frente a 42 en el conjunto del sector.
- **Probar las protecciones, como los extintores.** Una copia de seguridad no se sabe si funciona hasta que se necesita. Si puede estropearse sin avisar más o menos una vez cada dos años y solo se prueba una vez al año, hay aproximadamente una posibilidad entre cinco de que falle justo cuando haga falta. Probándola cada trimestre, baja a alrededor del 6 %.
- **Actualizar en las paradas programadas**, como cualquier otra intervención.
- **Rediseñar cuando no hay otra opción.** Si nada basta ante un riesgo grave para la seguridad, hay que separar redes o añadir protecciones mecánicas: una válvula de alivio no tiene software que se pueda atacar.
- **Cerrar la puerta del propio mantenimiento.** El portátil del técnico, la memoria USB o la conexión remota del fabricante son vías de entrada habituales. Igual que hay permisos de trabajo para intervenir en una máquina, debería haberlos para conectarse a ella.

> **[FIGURA 2]** `figuras/figura2_curva_PF_ciberataque.png`
> *Pie:* La «curva P-F» de un ciberataque: entre la entrada del atacante y el daño en la planta hay una ventana para detectarlo y frenarlo.

## Cuatro medidas que marcan la diferencia

- **Separar las redes**, como los compartimentos estancos de un barco: si entra agua en uno, el barco no se hunde. Separar la red de oficina de la de planta, y dentro de esta las zonas críticas, evita que un correo malicioso acabe parando la producción.
- **Vigilar en tiempo real.** Hay sistemas que aprenden cómo se comunican normalmente los equipos de la planta y avisan cuando aparece algo extraño, igual que un analizador de vibraciones avisa de un cambio en el espectro.
- **Controlar quién entra.** Doble verificación en los accesos, los permisos justos para cada persona, control de memorias USB y accesos remotos de proveedores por una única puerta, autorizados y grabados. El ataque que paró Toyota entró en su proveedor por un equipo de conexión remota.
- **Prepararse para recuperarse.** Simulacros como los de incendio, con informática, operación y mantenimiento; copias de seguridad desconectadas y probadas; repuestos preparados, y personal entrenado para operar en manual. Norsk Hydro mantuvo parte de su producción gracias al trabajo manual; Maersk se salvó por un golpe de suerte.

> **«La recuperación hay que diseñarla, no confiarla al azar.»**

## Las cuentas: ¿merece la pena invertir?

Pensemos en una planta de fabricación de tamaño medio en la que cada hora de parada cuesta 25.000 euros entre producción perdida, costes fijos y personal sin actividad, una cifra prudente comparada con las de Siemens.

- **Sin preparación**, un ataque que bloquea el centro de control obliga a parar diez días. Entre la parada (6 millones de euros), la respuesta y reconstrucción de sistemas (0,9 millones) y el rearranque y las penalizaciones (0,6 millones), el incidente cuesta **7,5 millones de euros**.
- **Con las cuatro medidas anteriores**, el ataque es menos probable y, si se produce, la parada se reduce a dos días: **1,6 millones de euros**.
- **Las medidas cuestan unos 320.000 euros al año**: 700.000 euros de inversión repartidos en cinco años y 180.000 euros anuales de funcionamiento.

Si sin protección cabe esperar un ataque grave cada diez años y con ella uno cada veinticinco, la pérdida media anual baja de 750.000 euros a unos 64.000. Se evitan unos 690.000 euros de pérdidas al año con un gasto de 320.000: cada euro invertido ahorra más de dos, y la inversión se recupera en menos de año y medio. Tres ideas merecen subrayarse:

1. **Lo que más rinde es acortar la recuperación.** Las medidas que reducen el tiempo de parada ahorran más que las que solo reducen la probabilidad del ataque: unos 590.000 euros al año frente a 450.000. Cada hora de parada evitada vale 25.000 euros.
2. **Compensa aunque el ataque sea poco probable.** Incluso si el ataque grave llegara solo una vez cada veinte años, la inversión seguiría compensando.
3. **El año malo lo cambia todo.** Un solo ataque sin preparación cuesta más de 23 veces lo que cuesta protegerse un año. En quince años, las medidas suman unos 4,8 millones de euros: menos que un único incidente.

Las cifras son ilustrativas y cada planta debe hacer sus cuentas, pero el razonamiento sirve para cualquier instalación.

> **[FIGURA 3]** `figuras/figura3_coste_ataque_vs_proteccion.png`
> *Pie:* Coste de un ataque con y sin preparación, frente al coste anual de protegerse (caso ilustrativo).

## No hay fiabilidad sin ciberseguridad

El ciberataque es ya una forma más de avería, con cuatro particularidades: no avisa, rompe a la vez lo que estaba duplicado, puede esconderse y tarda mucho en repararse. Por eso su impacto no se mide tanto en equipos dañados como en días de producción perdidos. La buena noticia es que los profesionales del mantenimiento ya tienen las herramientas para gestionarlo. Cinco recomendaciones para empezar mañana mismo:

1. Registrar en el GMAO la causa «ciberataque», para no confundir las averías provocadas con fallos técnicos.
2. Incluir los fallos de origen cibernético en el AMFE y el RCM de los equipos críticos.
3. Medir y ensayar el tiempo de recuperación ante un ciberataque como un indicador de fiabilidad más.
4. Crear equipos mixtos de mantenimiento, operación y ciberseguridad: nadie conoce mejor la planta que quien la mantiene.
5. Tener en cuenta la ciberseguridad desde la compra y el diseño de los equipos, cuando resulta más barata.

En una planta digitalizada, fiabilidad y ciberseguridad ya no son dos disciplinas distintas. Son la misma.

---

**Para saber más**

- Dragos (2026). *OT/ICS Cybersecurity Year in Review 2026*.
- Mandiant (2026). *M-Trends 2026*.
- Siemens (2024). *The True Cost of Downtime 2024*.
- Cyber Monitoring Centre (2025). Evaluación del ciberataque a Jaguar Land Rover.
- Greenberg, A. (2018). «The Untold Story of NotPetya». *Wired*.
- Normas de referencia: IEC 62443 (ciberseguridad industrial), IEC 60812 (AMFE) y SAE JA1011 (RCM).
