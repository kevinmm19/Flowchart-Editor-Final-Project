<center>
Editor de Diagramas de Flujo
============================
----------
</center>
<center>
### Documentaci�n de Aplicaci�n III Etapa
</center>

<center>
### Tecnol�gico de Costa Rica</center>
<center>
### Escuela de Ingenier�a en Computaci�n</center>
<center>
### Curso: Introducci�n al Dise�o de Interfaces Gr�ficas de Usuario</center>
<center>
### Profesor: Armando Arce Orozco</center>

<center>
### Cristina Valverde Mora - 200844549</center>
<center>
### Kevin Mart�nez Montero - 201029891</center>
<center>
### II Semestre 2012</center>

----------

##Introducci�n

La presente documentaci�n se refiere a la tercera etapa del proyecto, la cual incluye la funcionalidad completa del editor de diagramas de flujo asignado, adem�s de los cambios hechos en el dise�o del mismo.
 
La implementaci�n del editor se hizo de forma din�mica para esta tercera etapa del proyecto, por lo que se muestra  las funcionalidades principales del editor, incorporando interacciones. Las funcionalidades principales del editor consisten en la carga, despliegue, edici�n y guardado de diagramas de flujo en disco as� como la creaci�n de diagramas flujo desde la misma aplicaci�n.
 
Para la implementaci�n del editor y visualizador de diagramas de flujo, se  hace uso de un h�brido entre Adobe Air y Bootstrap, como ambiente gr�fico y herramienta de desarrollo. Adem�s se utiliza la librer�a Jointjs para dibujar los distintos componentes de los diagramas de flujo, tambi�n  se describen las decisiones de implementaci�n tomadas, las estructuras de datos utilizadas y se hace un an�lisis de las caracter�sticas del editor utilizado.
 
Para probar la funcionalidad alcanzada en este proyecto se muestran las pruebas realizadas  al editor para verificar que las funcionalidades funcionen bien,  esto se hizo utilizando un conjunto de datos de prueba espec�ficos. 

Se explica a profundidad el editor desarrollado, el cual es de diagramas de flujo,  junto con las interacciones y caracter�sticas avanzadas que se incorporaron a la aplicaci�n en esta etapa del proyecto.

Para esta etapa se incluyen adem�s cambios en el dise�o de la interfaz, los cuales consisten en: cambiar el tema de la interfaz, agregar una barra de botones y una ayuda.

Finalmente, se presentar�n las conclusiones de la tercera etapa del proyecto las cuales estar�n basadas en las limitaciones observadas y posibles mejoras (lista TO DO) de la aplicaci�n.

----------

## Descripci�n del contenido a desplegar

Para este proyecto el contenido a desplegar son los diagramas de flujo, los cuales representan algoritmos o procesos, donde cada s�mbolo utilizado tiene un �nico significado, pero puede ser representado por diversas figuras. A continuaci�n se muestra una tabla con los s�mbolos y las figuras que los representan:

--------------------------------------------------
S�mbolo	-> Figura
--------------------------------------------------
Inicio	-> Rect�ngulo redondeado
--------------------------------------------------
Fin	-> Rect�ngulo redondeado
--------------------------------------------------
Flujo de control	-> Flechas
--------------------------------------------------
Pasos de proceso gen�ricos	-> Rect�ngulo
--------------------------------------------------
Paso de decisi�n 	-> Rombo
--------------------------------------------------

----------

##Definici�n de estructuras de datos (formato) utilizadas

###Funciones de inicializacion

function getPaper(): esta funci�n lo que hace es crear una instancia Joint.paper en el panel de visualizaci�n , lugar en el que se desplegar�n los elementos del diagrama que se esta construyendo.

###Funciones de menu y manejo de archivos

function replaceOne(): reemplaza la primera aparici�n que se encuentre en el textarea  seg�n los par�metros dados en el modal de replace.

function replace(search,replace): reemplaza la primera aparicion de search en textarea con el valor de replace.

function replaceAll(): reemplaza todas las apariciones que se encuentre en el textarea  seg�n los par�metros dados en el modal de replace.

function newfile(): crea un nuevo archivo en el editor

function openfile():  abre un archivo para desplegar en el visualizador

function saveAsfile(): guarda el archivo con el nombre especificado por el usuario.

function savefile(): guarda  las modificaciones hechas en el archivo actual.

function exit(): finaliza y cierra la aplicaci�n.

###Funciones del despliegue del flowchart en el panel de view

function update(): actualiza el visualizador de la aplicaci�n.

function draw(): dibuja en el visualizador basado en lo que hay en el editor.

function drawStartNode(label,color,sizeX,sizeY,w,h): dibuja un nodo Start con los valores de label,color,sizeX,sizeY,w y h.

function drawEndNode(label,color,sizeX,sizeY,w,h):dibuja un nodo End con los valores de label,color,sizeX,sizeY,w y h.

function drawBlockNode(label,color,sizeX,sizeY,w,h):dibuja un nodo Block con los valores de label,color,sizeX,sizeY,w y h.

function drawDecisionNode(label,color,sizeX,sizeY,w,h): dibuja un nodo Decision con los valores de label,color,sizeX,sizeY,w y h.

function drawLinkNode(source,destiny,label,color,array):dibuja un nodo Link con los valores de source,destiny,label,color,array. Con esto se enlaza a dos nodos de cualquier otro tipo.

function searchShape(name,array): ubica una figura en el array formado por todas las figuras del visualizador para aplicarle operaciones.

###Funciones de la barra de botones

function drawBegin():  agrega el tag <flowchart> al editor .

function drawFinish():agrega la secuencia de tags que representan un nodo Finish.

function drawStart(): agrega la secuencia de tags que representan un nodo Start.

function drawBlock(): agrega la secuencia de tags que representan un nodo Block. 

function drawDecision(): agrega la secuencia de tags que representan un nodo Decision.

function drawEnd(): agrega la secuencia de tags que representan un nodo End.

function drawLink(source,destiny): agrega la secuencia de tags que representan un nodo Link.

function edit(editId,editLabel,editColor,editX,editY,eleini,elefin): funci�n que se encarga de editar nodos del tipo Start, End, Block y Decision.

function deletee(editId,eleini,elefin):funci�n que se encarga de eliminar nodos del tipo Start, End, Block y Decision.

function deleteeLink(editId,eleini,elefin): funci�n que se encarga de eliminar nodos del tipo Link.

function editLink(editId,editLabel,editSource,editDestiny,editColor,eleini,elefin):funci�n que se encarga de editar nodos del tipo Link.

function add(addLabel,addColor,addX,addY,type): funci�n que se encarga de agregar nodos del tipo Start, End, Block y Decision.

function addLink(addLabel,addSource,addDestiny,addColor): funci�n que se encarga de agregar nodos del tipo Link.

function editSelect(editId,editLabel,editColor,editX,editY): funcion que filtra que tipo de nodo va a ser editado de acuerdo con el id.

function addSelect(addLabel,addColor,addX,addY):funcion que filtra que tipo de nodo va a ser agregado de acuerdo con el tipo seleccionado por el usuario.

function deleteSelect(deleteId):funcion que filtra que tipo de nodo va a ser eliminado de acuerdo con el id.

----------

##Forma de compilaci�n, ejecuci�n y utilizaci�n de la aplicaci�n

Para hacer uso del editor de diagramas de flujo es necesario tener instalada la aplicaci�n Adobe Air y tener descargadas las librerias del Framework Bootstrap de Twitter, Jointjs y JQuery que se demostrar�n en la jerarqu�a de archivos. Antes de compilar el programa es conveniente crear los archivos y directorios que utiliza la aplicaci�n para poder ejecutarla correctamente.

Primero se crea la jerarqu�a de archivos, a partir de los archivos que han sido proporcionados en el repositorio de github, de la siguiente manera:

    Flowchart Editor
      + source
         + bootstrap
             + cerulean
             + css
             + img
             + js
         + icons
             * Arrow.png
             * begin.png
             * block.png
             * end.png
             * finish.png
             * rombo.png
             * start.png
         + js
             * AIRAliases.js
             * FlowchartFunctions.js
             * joint.all.min.js
             * jquery-1.8.2.js
         * application.xml
         * Flowchart.html

Para la compilaci�n del programa es necesario tomar el archivo de extensi�n .coffee donde se tiene escrita la l�gica de la aplicaci�n. Para generar el archivo en extensi�n .js es necesario llamar al compilador de coffeescript desde la l�nea de comandos. Se debe abrir la terminal de comandos de Windows y tener disponible el compilador de coffeescript llamado coffee.exe en el directorio donde se escribir� la siguiente l�nea: 


Para la ejecuci�n del programa se debe abrir la terminal de comandos de Windows y escribir la siguiente l�nea (se asume que el proyecto reside en el disco C y que el application.xml est� ubicado en el directorio actual):

<pre><code>
C:\AdobeAirSDK\bin\adl application.xml
</code></pre>

La compilaci�n y empaque de la aplicaci�n se puede realizar de la siguiente manera (desde un directorio Flowchart Editor):

<pre><code>
C:\AdobeAirSDK\bin\adt �certificate -cn SelfSigned 1024-RSA certificado.pfx MiClaveSecreta
</code></pre>

Y finalmente se debe agregar lo siguiente en una sola l�nea incluyendo el punto final:

<pre><code>
C:\AdobeAirSDK\bin\adt -package -storetype pkcs12 
    -keystore ..\certificado.pfx ..\TinyHMLEditor.air application.xml .
</code></pre>

De esta forma el editor est� listo para utilizarse. Las opciones disponibles a utilizar son las del men�, situado en la parte superior de la aplicaci�n, desde la opci�n File donde se encuentran todas las opciones a utilizar Open, Open Recent, Save As, Save, New y Exit. Save y Save As guardan el contenido del panel izquierdo en un archivo XML. La opci�n de Exit sirve para cerrar la aplicaci�n en caso de que ya no se desee trabajar en el editor. La opci�n de Open se encarga de abrir una nueva ventana donde el usuario pueda recorrer los directorios que desee y seleccionar un diagrama de flujo en formato XML, el cual el editor leer� y a partir de esto lo desplegar� en la ventana de trabajo situada en la parte derecha del editor.

El men� tambi�n incluye las funciones de edici�n del diagrama de flujo actual. Tales opciones son: Edit (Edit Node y Edit Link), Add (Add Node y Add Link), Delete (Delete Node y Delete Link) y Replace. Asi mismo, se presenta una barra de herramientas debajo del men� con siete distinos botones los cuales facilitar�n el dise�o de los diagramas de flujo del usuario. tales botones agregan nuevos elementos al diagrama y estos son: Begin, Start, Block, End, Decision, Link y Finish.

----------

##Ejemplos de datos a utilizar como pruebas

Los ejemplos de datos a utilizar como pruebas son diagramas de flujo en archivos con formato XML. Este formato nos permite crear un diagrama de flujo y guardarlo correctamente para su carga en nuevas ediciones. Es un formato �til para definir las caracter�sticas que contendr� cada diagrama de flujo de modo que el programa pueda definir un estilo capaz de leer correctamente cada diagrama de flujo tomado como archivo de entrada.

Para la carga de archivos se manejar� un formato espec�fico el cual se mostrar� a continuaci�n a modo de ejemplo. El primer ejemplo de un archivo en formato XML que representa un diagrama de flujo es el siguiente:

```
<code>
<flowchart>
<start>
			<id>s01</id>
			<label>Lamp doesn't work</label>
			<color>pink</color>
			<x>200</x>
			<y>5</y>
			<width>140</width>
			<height>60</height>
</start>
<decision>
			<id>d01</id>
			<label>Lamp plugged in?</label>
			<color>yellow</color>			
			<x>230</x>
			<y>110</y>
			<width>70</width>
			<height>70</height>
</decision>
		<end>
			<id>e01</id>
			<label>Plug in lamp</label>
			<color>lightgreen</color>			
			<x>400</x>
			<y>110</y>
			<width>140</width>
			<height>60</height>
                        </end>
		<decision>
			<id>d02</id>
			<label>Bulb burned out?</label>
			<color>yellow</color>			
			<x>230</x>
			<y>255</y>
			<width>70</width>
			<height>70</height>
                        </decision>
		<end>
			<id>e02</id>
			<label>Replace bulb</label>
			<color>lightgreen</color>			
			<x>400</x>
			<y>255</y>
			<width>140</width>
			<height>60</height>
                        </end>
<end>
			<id>e03</id>
			<label>Repair lamp</label>
			<color>lightgreen</color>			
			<x>200</x>
			<y>390</y>
			<width>140</width>
			<height>60</height>
</end>
		<link>
			<id>l1</id>
			<source>s01</source>
			<destiny>d01</destiny>
			<color>magenta</color>
		</link>
		<link>
			<id>l2</id>
			<source>d01</source>
			<destiny>d02</destiny>
			<label>Yes</label>
			<color>red</color>
		</link>
		<link>
			<id>l3</id>
			<source>d01</source>
			<destiny>e01</destiny>
			<label>No</label>
			<color>steelblue</color>
		</link>
		<link>
			<id>l4</id>
			<source>d02</source>
			<destiny>e02</destiny>
			<label>Yes</label>
			<color>gold</color>
		</link>
		<link>
			<id>l5</id>
			<source>d02</source>
			<destiny>e03</destiny>
			<label>No</label>
			<color>darkcyan</color>
		</link>
</flowchart>
</code>
```

El diagrama de flujo que se desea crear es el siguiente:

![Alt text](http://upload.wikimedia.org/wikipedia/commons/thumb/9/91/LampFlowchart.svg/220px-LampFlowchart.svg.png)

Un segundo ejemplo que puede realizarse perfectamente en la aplicaci�n es el siguiente:

![Alt text](http://3.bp.blogspot.com/_JmIzs1RspX0/TDFbgDZnRnI/AAAAAAAAAFs/pB57qilCSdg/s1600/DIAGRAMA+DE+FLUJO2.jpg)

Un tercer ejemplo de un algoritmo que desea saber si un numero entero es par o impar puede describirse con el siguiente archivo XML de prueba:

```
<code>
<flowchart>
<start>
			<id>s01</id>
			<label>int x = number</label>
			<color>lightgreen</color>
			<x>200</x>
			<y>5</y>
			<width>140</width>
			<height>60</height>
</start>
<block>
			<id>b01</id>
			<label>int y = x%2</label>
			<color>pink</color>
			<x>200</x>
			<y>110</y>
			<width>140</width>
			<height>60</height>
</block>
<decision>
			<id>d01</id>
			<label>if(y==0)</label>
			<color>white</color>			
			<x>230</x>
			<y>230</y>
			<width>70</width>
			<height>70</height>
</decision>
		<end>
			<id>e01</id>
			<label>return "Even"</label>
			<color>lightblue</color>			
			<x>400</x>
			<y>230</y>
			<width>140</width>
			<height>60</height>
		</end>
		<end>
			<id>e02</id>
			<label>return "Odd"</label>
			<color>lightblue</color>			
			<x>200</x>
			<y>390</y>
			<width>140</width>
			<height>60</height>
		</end>
		<link>
			<id>l1</id>
			<source>s01</source>
			<destiny>b01</destiny>
			<color>red</color>
		</link>
		<link>
			<id>l2</id>
			<source>b01</source>
			<destiny>d01</destiny>
			<color>red</color>
		</link>
		<link>
			<id>l3</id>
			<source>d01</source>
			<destiny>e01</destiny>
			<label>true</label>
			<color>red</color>
		</link>
		<link>
			<id>l4</id>
			<source>d01</source>
			<destiny>e02</destiny>
			<label>false</label>
			<color>red</color>
		</link>
</flowchart>
</code>
```

El resultado ser�a algo similar al siguiente diagrama:

![Alt text](http://physics.nyu.edu/pine/pymanual/_images/flow_if_else.jpg)

----------

##Cambios en el dise�o

Para esta entrega el editor cuenta con varios cambios en su dise�o, los cuales consisten en el cambio de apariencia por medio del uso de temas nuevos en la aplicaci�n, cambios en la barra de botones previamente dise�ada y adem�s se incluye la opci�n de una ayuda dentro de la 
misma . Los temas utilizados sobre la aplicaci�n son los siguientes:

###Amelia

![Alt text](http://img685.imageshack.us/img685/1699/ameliay.png)

###Cerulean

![Alt text](http://img836.imageshack.us/img836/854/ceruleann.png)

###Simplex

![Alt text](http://img252.imageshack.us/img252/411/simplex.png)

###Superhero

![Alt text](http://img27.imageshack.us/img27/1391/superherop.png)

###United 

![Alt text](http://img850.imageshack.us/img850/2179/uniteds.png)

###Boottheme

![Alt text](http://img811.imageshack.us/img811/4936/boottheme01.png)

###Lavish Theme

![Alt text](http://img40.imageshack.us/img40/1180/lavish03.png)


A la barra de botones implementada anteriormente se le agregaron las opciones �new�, �open�,�save,�save as�, 

![Alt text](http://img443.imageshack.us/img443/562/baat.png)


Finalmente se le agreg� una opci�n de ayuda la cual muestra el siguiente texto.

![Alt text](http://imageshack.us/a/img145/879/ayuda1.png)

![Alt text](http://imageshack.us/a/img839/7435/ayuda2j.png)

![Alt text](http://imageshack.us/a/img687/1311/ayuda3f.png)

![Alt text](http://imageshack.us/a/img204/7659/ayuda4.png)




----------


##Limitaciones observadas y posibles mejoras (lista TO DO)

Las limitaciones encontradas para esta tercera etapa del proyecto fueron pocas con respecto a las etapas pasadas, pues el ambiente h�brido de Bootstrap, Adobe Air y Javascript no result� muy d�ficil de utilizar pero si se tuvieron ciertos problemas al tratar de implementar el empaquetamiento o la ejecuci�n de la aplicaci�n en Adobe Air. A continuaci�n se presentan las limitaciones observadas y posibles mejoras:

 * Adobe Air no permite utilizar la librer�a Jointjs pues al tratar de dibujar las figuras en el ambiente, este tira errores de tipo los cuales vienen indicados expl�citamente en la libreria de joint.all.min.js, por lo que su implementaci�n en Adobe Air no fue exitosa.
 * El uso de Adobe Air para la carga y manejo de archivos fue exitoso pues todos los archivos pueden cargarse y guardarse correctamente.
 * A partir de constantes pruebas se determina que los diagramas de flujo pueden realizarse sin problemas, pues la implementaci�n de los diagramas a partir de los archivos XML de prueba fue exitosa, pero esto es solo factible en HTML pues en Adobe Air se generan errores al utilizar la librer�a de Jointjs.
 * La funcionalidad de cargar archivos recientes no pudo realizarse, puesto que no se pudieron crear items dinamicos que representaran archivos para la opci�n de dropdown �File/Open Recent� de la aplicaci�n, esto porque el manejo de los dropdowns por Bootstrap es distinto al HTML puro, por lo que esta funcionalidad no fue exitosa.
 * Se esperan resolver los problemas de librer�as con Adobe Air pues la librer�a clave para la realizaci�n del proyecto es Jointjs.
 * La implementaci�n de distintos temas a la aplicaci�n fue exitosa, ya que los cambios que se requer�an para adaptar los distintos temas a la aplicaci�n eran minimos o innecesarios, por lo que se pudo alcanzar un mayor grado de elegancia de aplicaci�n en esta tercera etapa.

----------