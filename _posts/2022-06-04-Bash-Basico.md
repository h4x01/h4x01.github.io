---
layout: single
title: '<span class="projects">Bash Scripting Basico</span>'
excerpt: "Aprende las bases de bash, con guías utiles que podrás utilizar constantemente, crea tu primera script en bash y convierte en un pentester."
date: 2021-12-28
categories:
  - projects
tags:  
  - linux
  - windows
  - scripting
  - bash
  - shell
  - ubuntu
  - virtualization
show_time: true
---


## Movilidad en tu entorno de trabajo

Mostrar la ruta actual 
```bash
~$ pwd
```
Listar directorios
```bash
~$ ls
```

Creando nombre Aprendiendo-Bash
```bash
~$ mkdir Aprendiendo-Bash 
```

Ingresando al directorio recién creado "bash"
```bash
~$ cd !$ 
```
Crear fichero index.html
```bash
~$ touch index.html
```

Ingresando al directorio recién creado "bash"
```bash
~$ cp index  ../directory
```
Mover un directorio o fichero
```bash
~$ mv index  ../directory
```
Eliminar fichero
```bash
~$ rm file
```

Eliminar directorios
```bash
~$ rmdir direcoroty
```

Buscar fichero
```bash
~$ locate index.html
```

Encontrar
```bash
~$ find file
```
Filtrar
```bash
~$ grep word file.txt
```
cambiar de usuario o elevar privilegios
```bash
~$ sudo user 
```



Crear el fichero "-"
```bash
~$ touch -
```

Ingresando cadena de caracteres al fichero "-"
```bash
~$ echo "cadena de caracteres" > - 
```

Mostrar contenido del fichero que esta en "-"
```bash
~$ cat ./- 
```

Print working directory, imprimir directorio de trabajo
```bash
~$ pwd 
```

Mostrando el archivo desde su ruta absoluta
```bash
~$ cat /home/user/carpeta/bash/- 
```
Recepciona el output de pwd
```bash
~$ $(pwd)
```

Mostrar el contenido de "-"
```bash
~$ cat $(pwd)/- 
```

Mostrar el contenido de todos los ficheros que se encuentren en esa ruta
```bash
~$ cat $(pwd)/* 
```

Muestra el tiempo de ejecución de un comando
```bash
~$ time $(pwd) 
```

<br>
<hr>
<hr>

Creando un directo con espacios en blanco
```bash
~$ mkdir "espacio en blanco" 
```

Change directory, cambiamos de directorio
```bash
~$ cd "espacio en blanco" 
```

Mambiando de directorio
```bash
~$ cd espacio\ en\ blanco  
```

creando fichero
```
~$ touch "fichero con espacios" 
```

redirigiendo la salida del comando al fichero con espacios
```
~$ echo $(cat /etc/hosts) > fichero\ con\ espacios 
```

<br>
<hr>
**Expreciones Regulares**: secuencia de caracteres y metacaracteres que forma un patrón de búsqueda, para la búsqueda de patrones de cadenas de caracteres u operaciones de sustituciones.


Fuente <https://francisconi.org/linux/expresiones-regulares>
<hr>
<br>
mostrar el contenido del fichero
```
~$ cat "fichero con espacios" 
```

mostrar el contenido del fichero
```
~$ cat fichero\ con\ espacios 
```

mostrar el contenido del fichero que comienze con "fi" y posteriormente cualquier cosa "*"
```
~$ cat fi* 
```

mostrar el contenido del fichero que comienze con cualquier cosa "*" y termine en "os"
```
~$ cat *os 
```

mostrar el contenido de todos los ficheros de la ruta actual
```
~$ cat /home/user/carpeta/bash/"espacio en blanco"/* 
```

ostrar todo el contenido de todos los ficheros de la ruta actual
```
~$ cat "$(pwd)"/* 
```

mostar todo lo que se encuntre en este directorio o ruta
```
~$ cat * 
```

<br>
<hr>
**Sesión Tres**

<hr>

listar ficheros ocultos 
```
~$ ls -a 
```

mustrame todo el contenido partiendo de la ruta actual
```
~$ find . 
```

encuentrame solo los ficheros
```
~$ find -type f 
```

```
-printf : me imprima
~$ find -type f -printf "%f\t%u\t%g\t%m\n" | column -t 
   
   > %f : ficheros
   > t%p : de forma tabula me indiques la ruta absoluta
   > t%u : de forma tabulada  me indiques el usuario propietario
   > t%g : de forma tabulada me indiques el  grupo asignado
   > t%m : de forma tabulada me indiques el modo (permiso asignado a niver numerico )
   > \n : salto de linea, para formatear el output 
   > -t : formatea el output en una tabla
```

crear un fichero oculto
```
~$ touch .hidden 
```

agregando cadena de caracteres al fichero
```
~$ echo "este fichero no es visible" > .hidden 
``` 

cambiando de directorio a la ruta raiz
```
~$ cd / 
```

encuentrame el fichero ".hidden" partiendo del directorio actual
```
~$ find . -name .hidden 2>/dev/null 
```

```
xargs: ejecuta un comando de forma paralela, con el output del comando ejecutado anteriormente
```

encuntrame el fichero ".hidden" y asu vez muestrame su contenido
```
~$ find . -name .hidden | xargs cat 
```

encuentra el fichero con el contenido "este fichero"
```
~$ find . -type f | xargs grep "este fichero" 2>/dev/null 
```

<br>
<hr>
**Sesión Cuatro**
<hr>

```
permisos en linux
read
.rwxrwxrwx .hidden 
write
r - 4 
execute
w - 2 
x - 1 
(rwx)  (--x) (--x)
 2^0   2^0
 111    001   001 
 2^0
 2^1
 2^2
   6     1      1
```

creando usuario pepito (por defecto se crea un grupo con su mismo nombre)
```
~$ sudo useradd pepito 
```

creando directorio
```
~$ mkdir directorio_pepito 
```

change group, asignando el grupo pepito a la carpeta "directorio_pepito"
```
~$ chgrp pepito directorio_pepito 
```

asignando a pepito como usuario propietario de la carpeta
```
~$ chown pepito directorio_pepito 
```

asignando usuario y grupo a la carpeta "directorio_pepito"
```
~$ chown pepito:pepito directorio_pepito 
```

asignando privilegio especial para no eliminar el archivo (ni siquiera root)
```
~$ chattr +i -V .hidden 
```

ver los privilegios especiales
```
~$ lsattr 
```

creando el "fichero2" y a su vez dirigiendome a la ruta raiz
```
~$ touch fichero2 && cd / 
```

encuntrame al fichero que comience con "fich" y cualquier cosa "*"
```
~$ find . -name "fich*" 
```


mostrar la ruta absoluta del binario "file" dentro del PATH
```
~$ which file 
```

mostrar la ruta del PATH
```
~$ echo $PATH 
```

instalando herramienta en ubuntu
```
~$ sudo apt install mlocate 
```

creando la base de datos de los ficheros del sistema
```
~$ sudo updatedb 
```

realizando busqueda de "fichero"
```
~$ locate fichero 
```

creando archivo "script", asignando permiso de ejecución y editando el archivo
```
~$ touch script.sh && chmod +x script.sh && nano script.sh 
```

```bash
#!/bin/bash
echo -e "te encuentras en esta ruta [ $(pwd) ]"
```

determina el tipo y formato de un archivo (para realizar esto, hace uso de los "magic numbers")
```
~$ file script.sh
```

creando "fichero.txt" y editando fichero
```
~$ touch fichero.txt && nano fichero.txt 
```

ingresa esto en el "fichero.txt"
```
GIF8; 
```

nos mostrar un fichero GIF, esto se debe a los "magic numbers" (47 49 46 38 3B ...	)
```
~$ file fichero.txt 
```

<hr>
**Scrub**: escribe patrones de forma iterativa en archivos o dispositivos de disco para dificultar la recuperación de los datos


**Shred**: herramienta de eliminación de archivos de modo seguro

Fuente: <https://www.computertechblog.com/using-scrub-command-to-secure-erase-data-in-redhat-linux/>
				<https://www.welivesecurity.com/la-es/2014/11/24/como-hacer-borrado-seguro-shred-linux/>
<hr>
