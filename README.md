# Juego-tetris
Juego tetris


Código
Solicitudes de extracción
Más
Comprometerse
código final
 maestro
@delrosfer
delrosfer comprometido el 1 de julio de 2020
1 padre c168c38
cometer 45e9df9
Mostrando 1 archivo modificado con 26 adiciones y 5 eliminaciones .
  31 cambios: 26 adiciones y 5 eliminaciones31 
tetris.py
@@ -4,7 +4,7 @@

ventana  =  tortuga . Pantalla ()
ventana . título ( "Creando Tetris con Turtle" )
ventana . bgcolor ( " negro " )
ventana . bgcolor ( " verde claro " )
ventana . configuración ( ancho = 600 , alto = 800 )
ventana . trazador ( 0 )

@@ -42,7 +42,7 @@ def __init__(yo):
		t  = [[ 0 , 1 , 0 ],
		     [ 1 , 1 , 1 ]]

		formas  = [ cuadrado , línea_horizontal , línea_vertical , izquierda_l , derecha_l , izquierda_s , derecha_s ]
		formas  = [ cuadrado , línea_horizontal , línea_vertical , izquierda_l , derecha_l , izquierda_s , derecha_s , t ]

		#elegir una figura aleatoria cada vez
		yo mismo . forma  =  aleatorio . elección ( formas )
@@ -86,6 +86,24 @@ def can_move(self, grid):

		 resultado de retorno

	def  rotar ( self , grid ):
		#primero borrar la figura
		yo mismo . borrar_forma ( cuadrícula )
		forma_girada  = []
		para  x  en el  rango ( len ( self . forma [ 0 ])):
			nueva_fila  = []
			para  y  en  rango ( len ( self . forma ) - 1 , - 1 , - 1 ):
				nueva_fila . agregar ( auto . forma [ y ] [ x ])
			forma_girada . agregar ( nueva_fila )

		lado_derecho  =  yo . x  +  len ( forma_rotada [ 0 ])
		si  lado_derecho  <  len ( cuadrícula [ 0 ]):

			yo mismo . forma  =  forma_girada
			#actualizar antura y anchura
			yo mismo . altura  =  len ( auto . forma )
			yo mismo . ancho  =  largo ( self . forma [ 0 ])

cuadrícula  = [
	[ 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
	[ 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
@@ -121,6 +139,7 @@ def can_move(self, grid):
bolígrafo . forma ( "cuadrado" )
bolígrafo . setundobuffer ( Ninguno )


def  draw_grid ( pluma , cuadrícula ):
	bolígrafo . claro ()
	arriba  =  230
@@ -160,10 +179,11 @@ def check_grid(cuadrícula):
					cuadrícula [ copia_y ][ copia_x ] =  cuadrícula [ copia_y - 1 ][ copia_x ]

def  draw_score ( bolígrafo , puntuación ):
	bolígrafo . color ( "azul" )
	bolígrafo . esconder tortuga ()
	bolígrafo . ir a ( - 75 , 300 )
	bolígrafo . escribir ( " Puntuacion : {} " . formato ( partitura ), mover = False , alinear = "izquierda" , fuente = ( "Arial" , 20 , "normal" ))
	bolígrafo . tortuga de exhibición ()
	bolígrafo . escribir ( " Puntuación : {} " . formato ( puntuación ), mover = False , align = "izquierda" , fuente = ( "Arial" , 20 , "normal" ))


#crear la figura básica para iniciar el juego
forma  =  Forma ()
@@ -177,6 +197,7 @@ def draw_score(pluma, puntuación):
ventana . escuchar ()
ventana . onkeypress ( lambda : forma . move_left ( cuadrícula ), "Izquierda" )
ventana . onkeypress ( lambda : forma . move_right ( cuadrícula ), "Derecha" )
ventana . onkeypress ( lambda : forma . rotar ( cuadrícula ), "espacio" )

#colocar la puntuación a 0
puntuación  =  0
@@ -217,8 +238,8 @@ def draw_score(pluma, puntuación):

#dibujar la pantalla

	draw_score ( bolígrafo , puntuación )	
	draw_grid ( bolígrafo , cuadrícula )
	draw_score ( bolígrafo , puntuación )

	tiempo . dormir ( retraso )
