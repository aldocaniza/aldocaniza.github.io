- # [[Metodologia de la programacion]]
	- ## Ordenamiento Metodo Burbuja
		- ### Sintaxis
			-
			  ```c++
			  intercambio (&valor1, &valor2){
			    int temporal;
			      temporal = valor1;
			    	valor1 = valor2;
			    	valor2 = temporal;
			  }
			  
			  a = 10; b = 20;
			  intercambio (a,b);
			  
			  //resultado a=20 b=10;
			  ```
			-
			  ```c++
			  // 4,3,2,1,0
			  
			  for (i=0;i<5;i++){
			    for(j=i+1;j<5;j++){
			      if (vector[i] > vector[j]){
			       	intercambiar(vector[i],vector[j]); 
			      }
			    }
			  }
			  ```
		- & : Operador de Desreferencia
			- cuando en una funcion pasan parametros estos crean una copia de la variable se le conoce **"por valor"** si quieren pasar el valor original usar &, es por **"por referencia"**
		- Desbordamiento de pila #card
			- se le conoce como StackOverFlow
		- Se llama burbuja porque sube de abajo para arriba
	- ## Ejercicios
		- [corregir y otros esta bien.docx](../assets/corregir_y_otros_esta_bien_1727221057513_0.docx)
		- #### Ejercicio 1
			-
			  ```c++
			  //1.	Ordenar Vectores. (corrige los errores)
			  #include <iostream>
			  using namespace std;
			  int main(){
			  	int i,j,auxiliar;
			  	int n = 10;  
			  	int vector[10] ={1,2,3,4,5,6,7,8,9,10} ;
			  	
			  	//primero se ejecuta el segundo for, 
			  	//luego el de arriba, similar al parentesis 
			  	//dentro de un parentesis en matematicas
			  	for(i = 0;i < n;i++){
			  		for(j = 0;j <(n-1);j++){ 
			  		    if (vector[i] > vector[j]){ //este bloque hace el intercambio, dependiendo de la condicion ordena ASC (>) o DESC (<) 
			  				auxiliar     =  vector[i];
			  		      	vector[i]    =  vector[j];
			  		      	vector[j]    =  auxiliar;
			  	        }
			  	    }
			  	}
			  
			  	for(i = 0;i < n ;i++){
			  		cout  <<  vector[i]  << "\t"; // \t para dejar como tabulador
			  	}
			  	return 0;
			  }//version 1
			  ```
			-
			  ```c++
			  //1.	Ordenar Vectores. (corrige los errores)
			  #include <iostream>
			  using namespace std;
			  int main(){
			  	int i,j,auxiliar;
			  	int n = 10;  
			  	int vector[10] ={10,9,8,7,6,5,4,3,2,1} ;
			  	
			  	//primero se ejecuta el segundo for, 
			  	//luego el de arriba, similar al parentesis 
			  	//dentro de un parentesis en matematicas
			  	for(i = 0;i < n;i++){
			  		for(j = 0;j <(n-1);j++){ 
			  		    if (vector[i] < vector[j]){ //este bloque hace el intercambio, dependiendo de la condicion ordena ASC (>) o DESC (<) 
			  				auxiliar     =  vector[i];
			  		      	vector[i]    =  vector[j];
			  		      	vector[j]    =  auxiliar;
			  	        }
			  	    }
			  	}
			  
			  	for(i = 0;i < n ;i++){
			  		cout  <<  vector[i]  << "\t"; // \t para dejar como tabulador
			  	}
			  	return 0;
			  }//version 2 Ascendente
			  ```
			-
			  ```c++
			  //1.	Ordenar Vectores. (corrige los errores)
			  #include <iostream>
			  using namespace std;
			  int main(){
			  	int i,j,auxiliar;
			  	int n = 10;  
			  	int vector[10] ={10,9,8,7,6,5,4,3,2,1} ;
			  	
			  	//primero se ejecuta el segundo for, 
			  	//luego el de arriba, similar al parentesis 
			  	//dentro de un parentesis en matematicas
			  	for(i = 0;i < n;i++){
			  		for(j = i+1;j <(n);j++){ //i+1 empieza comparando el primer componente con el segundo
			  		    if (vector[i] > vector[j]){ //este bloque hace el intercambio, dependiendo de la condicion ordena ASC (>) o DESC (<) 
			  				auxiliar     =  vector[i];
			  		      	vector[i]    =  vector[j];
			  		      	vector[j]    =  auxiliar;
			  	        }
			  	    }
			  	}
			  
			  	for(i = 0;i < n ;i++){
			  		cout  <<  vector[i]  << "\t"; // \t para dejar como tabulador
			  	}
			  	return 0;
			  }//version 3 Ascendente con i+1
			  ```
			-
			  ```c++
			  #include<iostream>
			  using namespace std;
			  void Imprimir_vector(int *vector, int n){
			    for(int i=0;i<n;i++){
			      cout<< vector[i]<<"\t";
			    }
			    cout<<endl;
			  }
			  void Intercambiar(int &valor1, int &valor2){
			    int auxiliar = valor1;
			    valor1       = valor2;
			    valor2       = auxiliar;
			  }
			  void Ordenar_vector(int *vector, int n){
			    for(int i = 0;i < n;i++)
			      for(int j = 0;j <(n-1);j++) 
			        if (vector[i] > vector[j])
			          Intercambiar(vector[i],vector[j]);
			  }
			  int main(){
			    int n = 10;  
			    int vector[10] ={1,2,3,4,5,6,7,8,9,10} ;
			    Imprimir_vector(vector,n); //se imprime antes de ordenar    
			    Ordenar_vector(vector,n); //Se llama a la funcion de ordenar
			    Imprimir_vector(vector,n); //Se imprime despues de ordenar
			    
			    return 0;
			  }//Version 4 con funciones
			  ```
			-
				-
		-
		-
	- ## Consideraciones
		- \t para dejar como tabulador
		- \n para salto de linea
		- primero se ejecuta el segundo for, luego el de arriba, similar al parentesis dentro de un parentesis en matematicas
		- if(vector[i] > vector[j]) //dependiendo de la condicion ordena ASC (<) o DESC (>)
		- el *(Asterisco) es para pasar por referencia el vector (se usa cuando es un vector)
		  ```c++
		  int *vector	
		  ```
		- el &(Amspersan) es para pasar por referencia variables (se usa con las variables) 
		  ```c++
		  intercambio(&valor1,&valor2){}
		  ```
		- Si hay un for dentro de otro for se pueden quitar los corchetes {} y el codigo funcionaria igual
