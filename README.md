# Realizar un proyecto con Kubernets
Materia: Computación Tolerante a Fallas<br>
Maestro: MICHEL EMANUEL LOPEZ FRANCO<br>
Nombre: Diego Alonso Mercado Brizuela<br>
Carrera: Ingeniería en Computación<br>
Código: 215425636<br>
Fecha: 20/11/2023<br>
Sección: D06<br>
## Introducción
Kubernetes es una plataforma de sistema distribuido de código libre para la automatización del despliegue, ajuste de escala y manejo de aplicaciones en contenedores​ que fue originalmente diseñado por Google y donado a la Cloud Native Computing Foundation.
## Pruebas
## 1 Crear carpeta principal
<br>
Crearemos una carpeta con el nombre que queramos.
<br>
En este escenario, se creó con este nombre "MicroServicio"
## 2 Abrir una consola
Dentro de la consola, escribir "npm install -y"
<br>
Para que nos cree un proyecto node
<br>
Imprimirá en el navegador un mensaje
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia4.png">
### 2.1 Escribir en consola
Escribir "npm install express"
<br>
Para que nos instale la librería de express
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia1.png">
<br>
## 3 Ejecutar proyecto en local
<br>
Escribiremos en consola "node index.js"
<br>
Para ver lo que realiza el proyecto, iremos al navegador y escribiremos "localhost:30" que es el puerto donde lo abrimos
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia2.png">
## 4 Crear archivo "Dockerfile"
<br>
Crear archivo con lo siguiente
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia3.png">
<br>
Con este indicaremos que instalaremos: alpine, usaremos el proyecto principal y ejecutaremos el "index.js"
<br>
## 5 Abrir Docker
<br>
Abriremos "Docker Desktop"
<br>
## 6 Construir la imágen en Docker
<br>
Escribir en consola "docker build -t microservicio ."
<br>
Nombraremos la imágen como queramos, en este caso es "microservicio"
<br>
## 6.1 Asignar un tag a esta imagen
<br>
Con este comando "docker tag microservicio usuario/microservicio"
<br>
Van a poder cambiar el nombre de su imagen junto con su nombre de usuario en Docker en "pedro/microservicio"
<br>
## 7 Ejecutar imágen Dockerfile
<br>
Ejecutar "docker run --rm -d -p 30:30 microservicio"
<br>
Ejecutaremos la imágen que ya construimos previamente, en el puerto 30 y en segundo plano. Para verificar esto, podemos abrir de nuevo el navegador con "localhost:30"
<br>
## 7.1 Comprobar en Docker Desktop
<br>
Si vemos nuestro Docker Desktop veremos que se está ejecutando en segundo plano
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia5.png">
<br>
## 8 Iniciar sesión en Docker
<br>
Iniciaremos sesión para después subir la imágen a Docker Hub con este comando en consola "docker login"
<br>
## 8.1 Subir la imágen a Docker hub
<br>
Escribir en consola este comando "docker push usuario/microservicio"
<br>
## 9 Comprobar configuración en Docker
<br>
Para continuar necesitamos verificar si está activado el kubernetes en la configuración de Docker
<br>
## 9.1 Configuración
<br>
Nos iremos al Docker y en la parte superior derecha habrá un ícono de un engranaje
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia6.png">
<br>
Al ingresar, nos dirigiremos a la sección "kubernetes"
<br>
Después aparecerá la opción "Enable Kubernetes"
<br>
La activaremos y daremos en el botón "Apply & restart"
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia7.png">
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia8.png">
<br>
## 10 Creación de un cluster
<br>
Para verificar que todo esté bien escribiremos esto en consola "kubectl get node", si nos indica lo siguiente, quiere decir que todo está bien
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia9.png">
<br>
Ahora crearemos un recurso tipo deployment en nuestro cluster, para administrar el estado de cada contenedor y si falla alguno lo reemplazará con una copia. Con este comando "kubectl create deployment --image microservicio node"
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia10.png">
<br>
Cuando hicimos esto, nos creó un nodo y otro recurso llamado "replicaset". Lo podemos ver con este comando "kubectl get all"
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia11.png">
<br>
## 11 Verificar pods
<br>
Aquí podemos que se está ejecutando el pod creado anteriormente con este comando "kubectl get pods"
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia12.png">
<br>
Pero si eliminamos este pod con este comando "kubectl delete pod node-9c4f5bc4d-jqht7", podemos ver que se eliminó pero se crearon 2 pods más, gracias al deployment.
<br>
Cabe mencionar que el nombre del pod dependerá de tu docker, ya que los cambia
<br>
<img src="https://github.com/Diego3207/MicroservicioDocker/blob/main/Evidencia13.png">
# Conclusiones
Kubernetes es código abierto lo que te brinda la libertad de aprovechar su infraestructura propia (on-premises), híbrida o de nube pública, lo que le permite mover las cargas de trabajo sin esfuerzo dónde quiera.
