Compilador lexico, sintactico y semantico

Alumno: Vera Meza Fernando Daniel

Codigo: 214404155

Fecha: 07/12/2021

Materia: Seminario de Solucion de problemas de Traductores 2

Profesor: Michel Emanuel Lopez Franco

Sección: D02

Carrera: INCO

CENTRO UNIVERSITARIO DE CIENCIAS EXACTAS EN INGENIERÍAS CUCEI

Objetivo:

En la clase de Seminario de Traductores 2 tenemos que crear un codigo que pueda realizar un analisis lexico, un analisis sintactico, y un analisis semantico a un codigo que el usuario introduzca.

Como se realiza:

Analisis lexico:

El analisis lexico lo hacemos con un ciclo que va a estar obteniendo todos los datos que el usuario introduce y despues se pone a revisarlos uno por uno y categorizandolos

![ciclo lexico](https://user-images.githubusercontent.com/89429934/145030972-6c0fa97a-ea5b-4ca2-aaca-433b49832d5c.PNG)

Estos quedan guardados primero en una tabla de tokens, en el archivo de tokens:

![tokens](https://user-images.githubusercontent.com/89429934/145031048-26220dd8-ddfd-4be4-9e8d-cea7450613e7.PNG)

Y despues revisa los tokens:

![revisa tokens](https://user-images.githubusercontent.com/89429934/145031068-05bcb387-d989-4860-ad78-2561ca69c379.PNG)


Sintactico:

Una vez que se haya terminado el lexico, se pasa al sintactico, el cual por medio de unas reglas de produccion, contenidas en el archivo GR2slrRules.txt, las cuales son las siguientes:

Programa -> Definiciones

Definiciones -> ''

Definiciones -> Definicion Definiciones

Definicion -> DefVar

Definicion -> DefFunc

DefVar -> tipo id ListaVar ;

ListaVar -> ''

ListaVar -> , id ListaVar

DefFunc -> tipo id ( Parametros ) BloqFunc

Parametros -> ''

Parametros -> tipo id ListaParam

ListaParam -> ''

ListaParam -> , tipo id ListaParam

BloqFunc -> { DefLocales }

DefLocales -> ''

DefLocales -> DefLocal DefLocales

DefLocal -> DefVar

DefLocal -> Sentencia

Sentencias -> ''

Sentencias ->Sentencia Sentencias

Sentencia -> id = Expresion ;

Sentencia -> if ( Expresion ) SentenciaBloque Otro

Sentencia ->while ( Expresion ) Bloque

Sentencia -> return Expresion ;

Sentencia -> LlamadaFunc ;

Otro -> ''

Otro -> else SentenciaBloque

Bloque -> { Sentencias }

Argumentos -> ''

Argumentos -> Expresion ListaArgumentos

ListaArgumentos -> ''

ListaArgumentos ->, Expresion ListaArgumentos

Expresion -> LlamadaFunc

Expresion -> id

Expresion -> constante

LlamadaFunc -> id ( Argumentos )

SentenciaBloque -> Sentencia

SentenciaBloque -> Bloque

Expresion -> ( Expresion )

Expresion -> Expresion opSuma Expresion

Expresion -> Expresion opLogico Expresion

Expresion -> Expresion opMul Expresion

Expresion -> Expresion opRelac Expresion



el programa se dispone a hacer push y pop a una pila interna y realizar reducciones por medio de las reglas estipuladas:

![sintactico](https://user-images.githubusercontent.com/89429934/145031732-50fb636c-9694-4191-aae8-957e52444052.PNG)

![sintactico 2](https://user-images.githubusercontent.com/89429934/145031748-b83e6df6-07cb-4693-a2de-9452963f817e.PNG)

![sintactico 3](https://user-images.githubusercontent.com/89429934/145031764-f2e8403a-a6a9-4d91-ab4e-b36fd2ca2a5d.PNG)



Analisis semantico:

Despues de haber terminado se pasa al analisis semantico

en el analisis semantico, el programa ahora se dedida a revisar que el arbol de derivacion se pueda generar

![semantico](https://user-images.githubusercontent.com/89429934/145032048-a99fdde1-1190-4abc-ba7a-fb51c596bd01.PNG)

Y una vez terminado el arbol se hace en un archivo png y se guarda en la carpeta principal

![Arbol](https://user-images.githubusercontent.com/89429934/145032305-d9e6c54c-d6ff-46d7-a11e-86a9cfbfe4a5.PNG)

Finalmente para tener como que una manera que el usuario utilize la aplicacion sin tener que utilizar la consola del programa, se debe de abrir el archivo exe de Compiler.exe que esta en la carpena bin/debug/ de este proyecto

![analizador](https://user-images.githubusercontent.com/89429934/145032469-18678a1c-27e2-4c8f-a028-598834b192dd.PNG)


En si eso es lo que tengo, no logre hacer el nasm generando el codigo

Conclusiones:

El realizar esta actividad requiere de mucho tiempo y dedicacion, ademas de generar un codigo en el que se retomen muchos conceptos vistos con anterioridad en la carrera como lo son las pilas, los nodos, los ciclos, los automatas, y poner demaciados casos de acciones que nuestro programa puede tomar para llegar a un resultado
