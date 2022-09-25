# CI-CD-Docker-GitHub-Actions-Kubernetes
Ejemplo de un CI/CD completo Github Actions.

Requisitos:

* Docker y Minikube instalados.


Este tutorial realiza un recorrido completo para desplegar un CI/CD básico desde un Archivo Dockerfile hasta el despliegue del deployment correspondiente en Kubernetes.

Para facilitar la práctica, clonamos el directorio que contiene este documento y el resto de archivos que necesitarás para realizar la práctica.

En la terminal ejecuta.
```
cd ~

git clone https://github.com/antsala/CI-CD-Docker-GitHub-Actions-Kubernetes.git
```



## Ejercicio 1: Crear un repositorio nuevo en ***Github*** y clonarlo.

En ***GitHub*** creamos un repositorio llamado ***CI-CD-Test***.
Nota: El nombre del repositorio puedes cambiarlo a tu gusto.
Nota: Si ya has realizado este laboratorio antes, elimina el repo y vuelve a crearlo desde cero.

En la terminal vamos a clonar el repositorio remoto.
Nota. Tendrás que poner la URL correcta de tu repositorio.
```
cd ~

git clone https://github.com/antsala/CI-CD-Test.git
```

Entramos en el directorio que se acaba de crear.
```
cd CI-CD-Test
```

Vamos a copiar algunos archivos necesarios desde el repositorio ***CI-CD-Docker-GitHub-Actions-Kubernetes*** a este directorio.
```
cp -r ~/CI-CD-Docker-GitHub-Actions-Kubernetes/helloContainer/ .

cp ~/CI-CD-Docker-GitHub-Actions-Kubernetes/Dockerfile .
```

Como puedes ver en la siguiente imagen, tenemos el ***Dockerfile*** que genera la imagen. En la carpeta ***helloContainer*** está el código fuente de la aplicación.

![Archivos copiados](./img/202209251430.png)

Para poder ejecutar comandos ***Git*** debemos tener configurado el ***nombre de usuario*** y el ***email***.
```
git config --global user.name "<Por aqui tu nombre>"

git config --global user.email "<Por aqui tu email>"
```

Procedemos a agregar el archivo y la carpeta al ***staging***. En la terminal, escribimos.
```
git add Dockerfile

git add helloContainer
```

Comprobamos que todo es correcto.
```
git status
```

El resultado debe ser el siguiente.

![Git status](./img/202209251438.png)

Hacemos un commit.
```
git commit -m "Commit inicial"
```

Actualizamos el repositorio remoto. Desde el 13 de Agosto de 2021, ***GitHub*** ya no permite usar el password para autenticar las operaciones de ***git***. 

Debemos generar un ***PAT*** (Personal Access Token). Para ello, desde la página web de ***GitHub***, desplegamos el perfil y entramos en la opción ***Settings/Developer Settings/Personal Access Token/Generate New Token***.

Rellenamos el formulario.

* En ***Note*** escribimos un nombre que identifique la utilidad del ***token oauth*** que estamos creando.

* También debemos indicar el ámbito del acceso que estamos concediendo. Elegimos ***Full control of private repositories***.

La imagen resume la configuración correcta.

![PAT](./img/202209251457.png)

Hacia la parte final de la página web encontraremos el botón ***Generate token***, en el que hacemos clic.

Copiamos el token de acceso en el portapapeles. Es importante tener en cuenta que ya no lo podremos visualizar más y, si lo perdemos, será necesario crear un ***PAT*** nuevo.


En la terminal escribimos.

```
git push
```

Nos pedirá el nombre de usuario de GitHub y como password, pegamos el que tenemos copiado en el portapapeles.

Ya tenemos el código fuente de la app y el Dockerfile para general la imagen en GitHub.


## Ejercicio 2: Contenerizar la aplicación.

Usamos la aplicación ***helloContainer*** cuya finalidad es la de levantar un servidor web en el puerto ***8080***. Cuando te conectas a él, responde mostrando en nombre de la máquina y las IPs que tiene configurada.

Vamos a abrir el archivo ***helloContainer.go*** que tiene el código fuente de la aplicación. Usa tu editor preferido (en este tutorial usamos ***nano***)
```
nano helloContainer/helloContainer.go
```




