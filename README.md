# st0263-Proyecto-2

##Instructivo Paso a Paso:

### Creación y configuración inicial de instancias.
Primero, cree 3 máquinas virtuales en GCP. Llame a una de ellas microk8s-master, y a las otras dos microk8s-worker-1 y microk8s-worker-2, respectivamente. Para las tres máquinas utilice la imagen de Ubuntu, y cambie el almacenamiento a 20 gb. Habilite también las conexiones HTTP, HTTPS, y las verificaciones del balanceador.

### Configuración inicial de instancia master.
Conéctese a la instancia de microk8s-master a través de SSH.
Ejecute el comando ```sudo apt update```.
Después, ejecute el comando ```sudo snap install microk8s --classic```.
Para realizar una verificación, ejecute el comando ```microk8s status --wait-ready```.
Saldrá entonces un mensaje como el siguiente:
![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)
Proceda a ejecutar individualmente los comandos que le solicitan ahí.
```sudo usermod -a -G microk8s etrujilloc```
```mkdir .kube```
```sudo chown -R etrujilloc ~/.kube```

Reinicie la conexión cerrando la consola y volviéndola a abrir.
Vuelva a ejecutar el comando ```microk8s status --wait-ready```.
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

Ahora, ejecute el comando ```microk8s enable dashboard dns registry istio```
Con este comando podrá instalar los plugins necesarios para microk8s.

Ahora, habilite el plugin necesario para utilizar NGINX nativo con el comando ```microk8s enable ingress```.

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. Para ello, ejecute el comando ```alias kubectl="microk8s kubectl"```. Así, ya solo debera usar el prefijo ```kubectl```.

Ahora, finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-worker-1```.

### Configuración inicial de instancia worker 1.
Una vez conectado en la instancia, se van a ejecutar los mismos comandos usados para la instancia master. Estos se describen a continuación nuevamente.

- Ejecute el comando ```sudo apt update```.
- Después, ejecute el comando ```sudo snap install microk8s --classic```.
- Para realizar una verificación, ejecute el comando ```microk8s status --wait-ready```.
Saldrá entonces un mensaje como el siguiente:
![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)
- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
```sudo usermod -a -G microk8s etrujilloc```
```mkdir .kube```
```sudo chown -R etrujilloc ~/.kube```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
- Vuelva a ejecutar el comando ```microk8s status --wait-ready```.
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando ```microk8s enable dashboard dns registry istio```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Ahora, habilite el plugin necesario para utilizar NGINX nativo con el comando ```microk8s enable ingress```.

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. Para ello, ejecute el comando ```alias kubectl="microk8s kubectl"```. Así, ya solo debera usar el prefijo ```kubectl```.

Ahora, finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-worker-1```.


### Configuración inicial de instancia worker 2.
Una vez conectado en la instancia, se van a ejecutar los mismos comandos usados para la instancia master. Estos se describen a continuación nuevamente.

- Ejecute el comando ```sudo apt update```.
- Después, ejecute el comando ```sudo snap install microk8s --classic```.
- Para realizar una verificación, ejecute el comando ```microk8s status --wait-ready```.
Saldrá entonces un mensaje como el siguiente:
![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)
- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
```sudo usermod -a -G microk8s etrujilloc```
```mkdir .kube```
```sudo chown -R etrujilloc ~/.kube```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
- Vuelva a ejecutar el comando ```microk8s status --wait-ready```.
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando ```microk8s enable dashboard dns registry istio```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Ahora, habilite el plugin necesario para utilizar NGINX nativo con el comando ```microk8s enable ingress```.

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. Para ello, ejecute el comando ```alias kubectl="microk8s kubectl"```. Así, ya solo debera usar el prefijo ```kubectl```.

Ahora, finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-master``` nuevamente.

### Creación del clúster.

En la instancia master ejecute el comando ```microk8s add-node```
Le mostrará entonces un comando que debe ejecutar en la instancia ```microk8s-worker-1```. Ejecútelo allí.
Una vez le diga que se conectó al cluster satisfactoriamente ejecute nuevamente el mismo comando en la instancia master. Nuevamente, ejecute el comando que se le muestre en la consola peroe sta vez en la instancia ```microk8s-worker-2```. 

Cuando ejecute el comando ```kubectl get nodes``` en la instancia master, después de haber hecho lo anterior, podrá ver los dos nodos workers recién añadidos al clúster.
![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/ca8be860-01a9-47fa-bdee-2a7c23c38577)






