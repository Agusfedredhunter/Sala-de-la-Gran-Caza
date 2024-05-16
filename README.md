1A: Tiempo de procesamiento de SINHILOS.PY: 5.63 segundos, 5.62 segundos, 5.52 segundos 
Tiempo de procesamiento de CONHILOS.PY: 4.43 segundos, 4.42 segundos, 4.53 segundos, 4.43 segundos 

1B: Son iguales, pero con pequeñas diferencias entre sí en los números de los milisegundos

1C: SUMA_RESTA.PY

1)	0.417
2)	0.465
3)	0.349
4)	0.269
5)	0.32
6)	0.284
7)	0.256
8)	0.327
9)	0.297
10)	0.28

SIN EL # 

1)	0.385
2)	0.267
3)	0.273
4)	0.298
5)	0.281
6)	0.358
7)	0.275
8)	0.293
9)	0.278
10)	0.285

Lo que paso fue que, con los comentarios, al inicio el programa tardaba un poco más en correr hasta que después llego hasta el rango de 200 milisegundos. Pero después de descomentar el programa, el procesamiento del programa no subió a más de 385 milisegundos por lo que se puede decir que se aceleró un poco. 

ACT 2

2A) #include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#define NUMBER_OF_THREADS 2
#define CANTIDAD_INICIAL_HAMBURGUESAS 20
int cantidad_restante_hamburguesas = CANTIDAD_INICIAL_HAMBURGUESAS;
int turno = 0;

while(turno!=(int)tid);

void *comer_hamburguesa(void *tid)
{
	while (1 == 1) 
	{ 
		
    // INICIO DE LA ZONA CRÍTICA
		if (cantidad_restante_hamburguesas > 0)
		{
			printf("Hola! soy el hilo(comensal) %d , me voy a comer una hamburguesa ! ya que todavia queda/n %d \n", (int) tid, cantidad_restante_hamburguesas);
			cantidad_restante_hamburguesas--; // me como una hamburguesa
			turno = (turno + 1)% NUMBER_OF_THREADS;
		}
		else
		{
			printf("SE TERMINARON LAS HAMBURGUESAS :( \n");

			pthread_exit(NULL); // forzar terminacion del hilo
		}
    // SALIDA DE LA ZONA CRÍTICA   

	}
}

int main(int argc, char *argv[])
{
	pthread_t threads[NUMBER_OF_THREADS];
	int status, i, ret;
	for (int i = 0; i < NUMBER_OF_THREADS; i++)
	{
		printf("Hola!, soy el hilo principal. Estoy creando el hilo %d \n", i);
		status = pthread_create(&threads[i], NULL, comer_hamburguesa, (void *)i);
		if (status != 0)
		{
			printf("Algo salio mal, al crear el hilo recibi el codigo de error %d \n", status);
			exit(-1);
		}
	}

	for (i = 0; i < NUMBER_OF_THREADS; i++)
	{
		void *retval;
		ret = pthread_join(threads[i], &retval); // espero por la terminacion de los hilos que cree
		turno = (turno + 1)% NUMBER_OF_THREADS
	}
	pthread_exit(NULL); // como los hilos que cree ya terminaron de ejecutarse, termino yo tambien.
}

2B)![Captura de pantalla 2024-05-14 231922](https://github.com/Agusfedredhunter/Sala-de-la-Gran-Caza/assets/167997966/9801a4ec-4de2-4929-b64b-497be2ee2b44)



