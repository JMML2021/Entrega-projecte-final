# Entrega-projecte-final

La puntualitat i el preu son les dos coses que els passatgers més valorem a l´hora de valorar una companyia Aérea. En aquest cast, tinc que esbrinar quin es la puntualitat d’una companyia aèria en lo que ells denomina’n el tercer salt, fent servir unes bases de dades proporcionada per ells. 

Les bases de dades te varies columnes amb les dates de enlairament i aterrament de cada avió. Un avió en un dia fa varis “salts”. Primer tinc que adequar els camps temps a un format date per poder fer la resat de temps. Tinc que identificar el vols de cada avio per dia, ordenar-los per hora de sortida per poder identificar cada salt i crear una seqüencia. Això obligarà a treballar en un format de línia perquè el temps calculats de cada salt estiguin en una sola línia per després poder filtrar el fitxer per tenir tota la informació de un avió per dia, el tres salts. Amb això reduirem el temps de càlcul al simplificar la mida del arxiu en un 80% accelerant el procés. Pesem de 500.000 Líneas a 80.000.

Per el càlcul farem servir el concepte Error, i identificat amb E_xxxxx. Aquest error serà la diferencia entre el temps real versus el temps planificat, sent positiu quan hi ha retard i negatiu quan arriba abans d l’hora.

Una vegada el arxiu està muntat podrem fer els principals càlculs i poder fer estudis de Capacitat per veure quantes vegades una distribució hi cap dintre dels límits que hem fitxat com els límits superior e inferior (USL i LSL). Obtenint el valor de % de vols que la seva puntualitat es més gran de 0 o 10 minuts.
Dintre del estudi demostrarem que entre salts no hi ha relació en els retards. El primer salt es independent en un percentatge molt alt respecte al salt segon i tercer. Per demostrar això, farem servir una regressió logística. 

El procés serà:

Filtrarem els temps que el Error siguin més grans de 30 minuts. Aquet valor de 30 minuts, és escollit entre els experts d’aviació que van participar en aquest estudi i que representa el 3% del total dels vols. Fer aquest cribratge es per eliminar incidències mols aleatòries que no més aporten soroll al estudi.

Les dades son molt des-balancejades en la quantitat de vols que arriben tard. El 92% dels vols arriben a l’hora, i només un 8% tard. 

Però primer farem un Split de un 80% de vols que seran de  train i un 20% de test. Balancejaré les dades de train i crearé el model de “regressió logística”. Farem un “summary” i ens fixarem en els valors de les P_values. Tots els factors que no siguin més petits de 0.05 els rebutjarem. 

A l’estudi veurem que només per el retard del 3r salt, l’error en la sortida i l’error en el temps de vol, afecten. Amb aquest 2 paràmetres expliquem en un 78% el impacta del retard de l’avió, i la resta fins el 100% es soroll.

Demostrat aquesta falta de lligam entre retards i nº de salt, ens fixarem en el primer salt perquè es el que té menys elements exògens que afectin al retard. Veurem que el primer salt només el 62% dels vols surten a l’hora, sent sortir a l’hora, l`hora planificada. No acceptar 10 minuts de “cortesia” que per costum es fa, sinó sortir exactament en el moment establert. 

Es veurà que tots els salts tenen una variabilitat molt gran, i que este que reduir. Per demostrar això feren servir els “estudis de capacitat”.

