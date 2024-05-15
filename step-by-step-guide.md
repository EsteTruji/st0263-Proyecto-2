# st0263-Proyecto-2

## Instructivo Paso a Paso:

### Creación y configuración inicial de instancias.
Primero, cree 4 máquinas virtuales en GCP. Llame a una de ellas microk8s-master, y a otras dos microk8s-worker-1 y microk8s-worker-2, respectivamente, y finalmente a otra instancia llamada microk8s-nfs. Para las cuatro máquinas utilice la imagen de Ubuntu, y cambie el almacenamiento a 20 gb. Habilite también las conexiones HTTP, HTTPS, y las verificaciones del balanceador.

### Configuración inicial de instancia master.
- Conéctese a la instancia de microk8s-master a través de SSH.
  
- Ejecute el comando:

```
sudo apt update
```
  
- Después, ejecute el comando:
  
```
sudo snap install microk8s --classic
```
  
- Para realizar una verificación, ejecute el comando:
  
```
microk8s status --wait-ready
```
Saldrá entonces un mensaje como el siguiente:

![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)

- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
  
```
sudo usermod -a -G microk8s etrujilloc
```
```
mkdir .kube
```
```
sudo chown -R etrujilloc ~/.kube
```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
  
- Vuelva a ejecutar el comando:
  
```
microk8s status --wait-ready
```
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando:
  
```
microk8s enable dashboard dns registry istio
```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Después, habilite el plugin necesario para utilizar NGINX nativo con el comando:
  
```
microk8s enable ingress
```

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. 
Para ello, ejecute el comando:

```
alias kubectl="microk8s kubectl"
```
Así, ya solo debera usar el prefijo ```kubectl```.

- Finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-worker-1```.

### Configuración inicial de instancia worker 1.
- Conéctese a la instancia de microk8s-worker-1 a través de SSH.
  
- Ejecute el comando:

```
sudo apt update
```
  
- Después, ejecute el comando:
  
```
sudo snap install microk8s --classic
```
  
- Para realizar una verificación, ejecute el comando:
  
```
microk8s status --wait-ready
```
Saldrá entonces un mensaje como el siguiente:

![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)

- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
  
```
sudo usermod -a -G microk8s etrujilloc
```
```
mkdir .kube
```
```
sudo chown -R etrujilloc ~/.kube
```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
  
- Vuelva a ejecutar el comando:
  
```
microk8s status --wait-ready
```
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando:
  
```
microk8s enable dashboard dns registry istio
```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Después, habilite el plugin necesario para utilizar NGINX nativo con el comando:
  
```
microk8s enable ingress
```

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. 
Para ello, ejecute el comando:

```
alias kubectl="microk8s kubectl"
```
Así, ya solo debera usar el prefijo ```kubectl```.

- Finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-worker-2```.


### Configuración inicial de instancia worker 2.
- Conéctese a la instancia de microk8s-worker-2 a través de SSH.
  
- Ejecute el comando:

```
sudo apt update
```
  
- Después, ejecute el comando:
  
```
sudo snap install microk8s --classic
```
  
- Para realizar una verificación, ejecute el comando:
  
```
microk8s status --wait-ready
```
Saldrá entonces un mensaje como el siguiente:

![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)

- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
  
```
sudo usermod -a -G microk8s etrujilloc
```
```
mkdir .kube
```
```
sudo chown -R etrujilloc ~/.kube
```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
  
- Vuelva a ejecutar el comando:
  
```
microk8s status --wait-ready
```
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando:
  
```
microk8s enable dashboard dns registry istio
```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Después, habilite el plugin necesario para utilizar NGINX nativo con el comando:
  
```
microk8s enable ingress
```

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. 
Para ello, ejecute el comando:

```
alias kubectl="microk8s kubectl"
```
Así, ya solo debera usar el prefijo ```kubectl```.

- Finalice la conexión, e inicie una nueva a través de SSH con la instancia ```microk8s-master```, nuevamente.


### Configuración NFS.

Conéctese a la instancia microk8s-nfs a través de SSH.
  
- Ejecute el comando:

```
sudo apt update
```
  
- Después, ejecute el comando:
  
```
sudo snap install microk8s --classic
```
  
- Para realizar una verificación, ejecute el comando:
  
```
microk8s status --wait-ready
```
Saldrá entonces un mensaje como el siguiente:

![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/443f0b3f-ac09-4343-a47e-11652977718a)

- Proceda a ejecutar individualmente los comandos que le solicitan ahí.
  
```
sudo usermod -a -G microk8s etrujilloc
```
```
mkdir .kube
```
```
sudo chown -R etrujilloc ~/.kube
```

- Reinicie la conexión cerrando la consola y volviéndola a abrir.
  
- Vuelva a ejecutar el comando:
  
```
microk8s status --wait-ready
```
Le aparecerá ahora sí un mensaje que dice que microk8s está ejecutándose.

- Ahora, ejecute el comando:
  
```
microk8s enable dashboard dns registry istio
```
Con este comando podrá instalar los plugins necesarios para microk8s.

- Después, habilite el plugin necesario para utilizar NGINX nativo con el comando:
  
```
microk8s enable ingress
```

A partir de acá será necesario usar comandos que tienen el prefijo ```microk8s kubectl```. Sin embargo, esto puede ser largo y tornarse ineficiente en términos de escritura. Por lo tanto, usaremos un alias para evitar tener que escribirlo completo. 
Para ello, ejecute el comando:

```
alias kubectl="microk8s kubectl"
```
Así, ya solo debera usar el prefijo ```kubectl```.

- Proceda después a instalar el servidor NFS con el siguiente comando:

```
sudo apt update
sudo apt install nfs-kernel-server
```
- Ahora, cree el directorio que se compartirá:
```
sudo mkdir -p /mnt/wordpress
```
- Cambie el propietario del directorio:
```
sudo chown nobody:nogroup /mnt/wordpress
```
- Después, cambie los permisos del directorio:
```
sudo chmod 777 /mnt/wordpress
```
- Edite el archivo /etc/exports:
```
sudo nano /etc/exports
```
- Deberá añadir entonces la siguiente línea en el archivo recién creado y abierto:
```
/mnt/wordpress *(rw,sync,no_subtree_check)
```
- Guarde los cambios hechos en el archivo, y después reinicie el servicio de NFS:
```
sudo systemctl restart nfs-kernel-server
```

### Creación del clúster.

#### Configuración workers.
En la instancia master ejecute el comando:

```
microk8s add-node
```

Le mostrará entonces un comando que debe ejecutar en la instancia ```microk8s-worker-1```. Ejecútelo allí.
Una vez le diga que se conectó al cluster satisfactoriamente ejecute nuevamente el mismo comando en la instancia master. Nuevamente, ejecute el comando que se le muestre en la consola pero esta vez en la instancia ```microk8s-worker-2```. 

Cuando ejecute el comando 
```
kubectl get nodes
``` 
en la instancia master, después de haber hecho lo anterior, podrá ver los dos nodos workers recién añadidos al clúster.

![image](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/ca8be860-01a9-47fa-bdee-2a7c23c38577)

#### Configuración NFS.

Conectado a la instancia master por SSH, realice las siguientes acciones:

- Primero, habilite Helm3 y añada el repositorio de CSI Driver para NFS:
```
microk8s enable helm3
microk8s helm3 repo add csi-driver-nfs https://raw.githubusercontent.com/kubernetes-csi/csi-driver-nfs/master/charts
microk8s helm3 repo update
```

- Después, instale el driver para NFS:
  
```
microk8s helm3 install csi-driver-nfs csi-driver-nfs/csi-driver-nfs \
 --namespace kube-system \
 --set kubeletDir=/var/snap/microk8s/common/var/lib/kubelet
```

- Cree el StorageClass con el siguiente comando:
```
nano nfs-csi.yaml
```
- En ese archivo creado y abierto pegue lo siguiente:

```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: nfs-csi
provisioner: nfs.csi.k8s.io
parameters:
  server: 10.128.0.7
  share: /mnt/wordpress
reclaimPolicy: Delete
volumeBindingMode: Immediate
mountOptions:
  - hard
  - nfsvers=4.1
```

- Ahora, aplique el archivo nfs-csi.yaml:
```
kubectl apply -f nfs-csi.yaml
```
- Después de ello, cree el PersistentVolumeClaim con el siguiente comando:
```
nano nfs-pvc.yaml
```
- Después, en ese archivo recién creado y abierto coloque el siguiente contenido:
```
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: nfs-pvc
spec:
  storageClassName: nfs-csi
  accessModes: [ReadWriteOnce]
  resources:
    requests:
      storage: 5Gi
```
    
- Finalmente, aplique el archivo nfs-pvc.yaml:
```
kubectl apply -f nfs-pvc.yaml
```

#### Configuración Base de Datos y WordPress.

Conectado a la instancia microk8s-master, realice lo siguiente:

- Para la creación de un kustomization file, con el fin de almacenar un Secret con información de la base de datos, ejecute el siguiente comando cambiando el valor **YOUR_PASSWORD** por la contraseña que desee colocar para la base de datos:
```
cat <<EOF >./kustomization.yaml
secretGenerator:
- name: mysql-pass
  literals:
  - password=YOUR_PASSWORD
EOF
```

- Cree un archivo llamado ```mysql-pv-pvc.yaml```, el cual corresponderá al PersistentVolume y al PersistentVolumeClaim para MySQL, con el siguiente comando:
```
nano mysql-pv-pvc.yaml
```
- Coloque dentro del archivo recién creado y abierto el siguiente contenido:
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv-volume
  labels:
    type: local
spec:
  storageClassName: ""
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
  labels:
    app: wordpress
spec:
  accessModes:
    - ReadWriteOnce
  volumeName: mysql-pv-volume
  resources:
    requests:
      storage: 5Gi
```

- Después, cree otro archivo llamado ```mysql-deployment.yaml```, el cual corresponderá al deployment y al service para MySQL y la base de datos deseada, con el siguiente comando:
```
nano mysql-deployment.yaml
```
- Coloque dentro del archivo recién creado y abierto el siguiente contenido:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress-mysql
  labels:
    app: wordpress
spec:
  selector:
    matchLabels:
      app: wordpress
      tier: mysql
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: wordpress
        tier: mysql
    spec:
      containers:
      - image: mysql:8.0
        name: mysql
        env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-pass
              key: password
        - name: MYSQL_DATABASE
          value: wordpress
        - name: MYSQL_USER
          value: wordpress
        - name: MYSQL_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-pass
              key: password
        ports:
        - containerPort: 3306
          name: mysql
        volumeMounts:
        - name: mysql-persistent-storage
          mountPath: /var/lib/mysql
      volumes:
      - name: mysql-persistent-storage
        persistentVolumeClaim:
          claimName: mysql-pv-claim
---
apiVersion: v1
kind: Service
metadata:
  name: wordpress-mysql
  labels:
    app: wordpress
spec:
  ports:
  - port: 3306
  selector:
    app: wordpress
    tier: mysql
  clusterIP: None
```

- Después, cree otro archivo llamado ```wordpress-deployment.yaml```, el cual corresponderá al deployment, al service, y al PersistentVolumeClaim para WordPress, con el siguiente comando:
```
nano wordpress-deployment.yaml
```
- Coloque dentro del archivo recién creado y abierto el siguiente contenido:
```
apiVersion: v1
kind: Service
metadata:
  name: wordpress
  labels:
    app: wordpress
spec:
  ports:
    - port: 80
  selector:
    app: wordpress
    tier: frontend
  type: LoadBalancer
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: wp-pv-claim
  labels:
    app: wordpress
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: nfs-csi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress
  labels:
    app: wordpress
spec:
  selector:
    matchLabels:
      app: wordpress
      tier: frontend
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: wordpress
        tier: frontend
    spec:
      containers:
      - image: wordpress
        name: wordpress
        env:
        - name: WORDPRESS_DB_HOST
          value: wordpress-mysql
        - name: WORDPRESS_DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-pass
              key: password
        - name: WORDPRESS_DB_USER
          value: wordpress
        ports:
        - containerPort: 80
          name: wordpress
        volumeMounts:
        - name: wordpress-persistent-storage
          mountPath: /var/www/html
      volumes:
      - name: wordpress-persistent-storage
        persistentVolumeClaim:
          claimName: wp-pv-claim
```

- Después de crear los archivos anteriores, proceda a aplicar el manifiesto del archivo ```mysql-pv-pvc.yaml```, con el siguiente comando:
```
kubectl apply -f mysql-pv-pvc.yaml
```
- Ahora, ejecute el siguiente comando para añadir los deployments previamente creados al archivo kustomization:
```
cat <<EOF >>./kustomization.yaml
resources:
  - mysql-deployment.yaml
  - wordpress-deployment.yaml
EOF
```
- Proceda a aplicar dichos archivos con el comando a continuación:
```
kubectl apply -k ./
```

De esta forma, ya tiene WordPress y MySQL configurados y conectados correctamente. 

#### Configuración Load Balancer.
Continuando con la conexión a la instancia microk8s-master, realice las siguientes acciones:

- Primero, con el fin de redirigir las requests al dominio correspondiente al proyecto, diríjase al panel de su proveedor de dominio (en este caso, GoDaddy), y verifique que los registros A y CNAME concuerden con la imagen que se muestra a continuación:

![DNS-records](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/c66fc8ae-559e-44e3-83df-d397a8e651e5)


**Nota:** deberá cambiar la IP que ahí aparece por la IP pública correspondiente a la instancia microk8s-master que creó.

- Después de ello, se configurará el Ingress (Load Balancer), de tal forma que se pueda acceder con HTTPS, es decir, tenga los certificados correspondientes. Para ello, se habilitará el plugin de cert-manager con el comando a continuación:
```
microk8s enable cert-manager
```

- Ahora, proceda a crear un archivo llamado ```cluster-issuer.yaml``` para configurar una cuenta de correo con Let's Encrypt, con el comando a continuación:
```
nano cluster-issuer.yaml
```
- Coloque el siguiente contenido en el archivo recién creado y abierto:
```
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
 name: lets-encrypt
spec:
 acme:
   email: <EMAIL-ADDRESS>
   server: https://acme-v02.api.letsencrypt.org/directory
   privateKeySecretRef:
     # Secret resource that will be used to store the account's private key.
     name: lets-encrypt-priviate-key
   # Add a single challenge solver, HTTP01 using nginx
   solvers:
   - http01:
       ingress:
         class: public
```
**Nota:** deberá cambiar el valor <EMAIL-ADDRESS> por el correo con el cual desea cofigurar Let's Ecrypt.

- Proceda a aplicar dicho archivo con el comando:
```
kubectl apply -f cluster-issuer.yaml
```

- Ahora, pase a configurar el Ingress, para lo cual será necesario crear un archivo llamado ```nginx-ingress-2.yaml```, con el siguiente comando:
```
nano nginx-ingress-2.yaml
```
- Coloque dentro de ese archivo recién creado y abierto el siguiente contenido:
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
 name: wordpress-ingress
 annotations:
   cert-manager.io/cluster-issuer: lets-encrypt
spec:
 tls:
 - hosts:
   - <YOUR-DOMAIN>
   secretName: microbot-ingress-tls
 rules:
 - host: <YOUR-DOMAIN>
   http:
     paths:
     - backend:
         service:
           name: wordpress
           port:
             number: 80
       path: /
       pathType: Exact
```
**Nota:** deberá cambiar el valor <YOUR-DOMAIN> por su dominio correspondiente.
- Proceda a aplicar ese archivo con el comando:
```
kubectl apply -f nginx-ingress-2.yaml
```
**Nota:** deberá esperar unos momentos para que se creen los certificados TLS correspondientes y se almacenen en las carpetas respectivas. 

- Después de varios minutos, proceda a la siguiente sección.

#### Verificación del funcionamiento de la aplicación.

1. Proceda ahora a dirigirse desde su navegador web al dominio colocado en <YOUR-DOMAIN> previamente.
2. Le deberá aparecer entonces la página de configuración de WordPress.
3. Siga cada uno de los pasos que allí se le indiquen.
4. Una vez configurada completamente, acceda en otra pestaña a su dominio y ¡deberá ver su página completamente lista!

![Landing-page-HTTPS](https://github.com/EsteTruji/st0263-Proyecto-2/assets/82886890/3bcb6481-02f6-49f8-b8e0-469d40eec402)

