
# Info de la materia: ST0263 - Tópicos Especiales en Telemática

### Estudiantes:
  - Esteban Trujillo Carmona, etrujilloc@eafit.edu.co
  - Viviana Hoyos Sierra, vhoyoss@eafit.edu.co
  - Damian Duque López, daduquel@eafit.edu.co
  - Valentina Morales Villada, vmoralesv@eafit.edu.co

### Profesor: Edwin Montoya, emontoya@eafit.edu.co

# Reto 4 

# Video sustentación

[![Video](https://img.youtube.com/vi/6Vu73vi8l-g/0.jpg)](https://www.youtube.com/watch?v=6Vu73vi8l-g)

## 1. Breve descripción de la actividad
Se desplegó un CMS wordpress (app monolítica) en una arquitectura distribuida haciendo uso de tecnologías como Kubernets, proveedores de dominio como GoDaddy y servicios de Google Cloud Platform.

En este reto utilizamos los servicios de balanceador de cargas, Filestore y Cloud SQL nativos de google para satisfacer las necesidades de nuestra aplicación. utilizando un servicio administrado de NFS en la nube a partir de la API de Filestore para disponer del sistema de archivos. se desplegaron (PENDIENTE POR CONFIRMAR Y ANOTAR) maquinas virtuales en google cloud.



### 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

**NO FUNCIONALES**

-	**DISPONIBILIDAD:**
    -  Despliegue de  aplicación wordpress con varios pods utilizando Kubernetes.
    -  Implementar un balanceador de cargas basado en los servicios nativos de Google que reciba el tráfico web http de Internet con múltiples instancias de procesamiento.
   

**FUNCIONALES**
-	Almacenamiento en la capa de datos haciendo uso del servicio de bases de datos mysql ofrecido por Google.
- Almacenamiento de archivos implementado haciendo uso del servicio de NFS ofrecido por Google.
- Conexion de servicios de wordpress con el servicio NFS.



### 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

No logro obtener el certificado SSL para implementar https dentro de la aplicación.

## 2. Información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.

Se implementó para este proyecto la siguiente arquitectura:

![microck8s_final](https://github.com/EsteTruji/st0263-proyecto-2/assets/81714113/515290fc-fb60-4553-b6d2-7d8df11b2535)



## 3. Descripción del ambiente de ejecución lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.


**IPs utilizadas en el reto 4:**

**IPs Privadas:**

- **Servicio Kubernetes:** 10.103.192.1
- **Servicio Load balancer:** 10.103.193.248

**IPs Públicas:**
- **Servicio Load balancer:** 34.171.91.170
- **DataBase:** 35.192.174.33


Cabe resaltar que para el desarrollo y cumplimiento de este reto no fue necesario instalar ningun otro paquete o libreria adicional ya que todos los recursos utilizados son nativos de GCP.


## 4. Guía paso a paso de instalación y configuración

La guía paso a paso de este proyecto se encuentra en el archivo ```step-by-step-guide.md``` subido en este repositorio. De igual forma, se puede acceder a este desde el enlace a continuación:

[Step-by-Step-guide](https://github.com/EsteTruji/st0263-Proyecto-2/blob/main/step-by-step-guide.md)

## Referencias

[Install MicroK8s](https://microk8s.io/#install-microk8s)

[Use NFS for Persistent Volumes on MicroK8s](https://microk8s.io/docs/how-to-nfs)

[Example: Deploying WordPress and MySQL with Persistent Volumes](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)

[Deploying MySQL on Kubernetes](https://medium.com/@midejoseph24/deploying-mysql-on-kubernetes-16758a42a746)

[Addon: cert-manager](https://microk8s.io/docs/addon-cert-manager)






