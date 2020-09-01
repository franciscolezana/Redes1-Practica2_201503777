<img src="https://portal.ingenieria.usac.edu.gt/images/2019/logo/logo-fiusac.png"/>



**NOMBRE**: FRANCISCO HUMBERTO LEZANA RAMOS  
**CARNET**: 201503777  
**CURSO**: REDES DE COMPUTADORAS 1

# MANUAL DE CONFIGURACIÓN

## HERRAMIENTAS A UTILIZAR 

- GNS3
- Software de virtualización (VMWare o Virtual Box) instalados y configurado para uso con GNS3.
- Wireshark 

## TOPOLOGIA DE RED DEL PROYECTO 

La siguiente topología cuenta con 6 host de los cuales 5 son VPCS y 1 es una máquina virtual con un sistema tiny-linux para ahorrar recursos, podemos observar que los host se conectan a 3 switches distintos los cuales representan a los distintos departamentos de la empresa ( finanzas, ventas e informática) y estos se conectan entre sí por medio de un router el cuál será centro principal de comunicación.
<img src="/SS/TOPO.PNG"/>


## CONFIGURACIÓN DE LA TOPOLOGÍA DE RED EN GNS3

### DIRECCIONES IP DE LOS HOST

Para esta práctica se van a utilizar las siguientes direcciones IP, la X representan el 4to número de carnet del estudiante de derecha a izquierda. El carnet del usuario es 201503777 , se utilizará X:3 al momento de conectar los host. Las ips asignadas serán las siguientes: 

<img src="/SS/ips.png"/> 

Las subredes están dadas por la siguiente imagen:

<img src="/SS/subs.png"/> 

Las interfaces del router poseerán las siguientes ips:  

| NO.  | INTERFAZ | IP ASIGNADA    | MASCARA DE REDE |
| ---- | -------- | -------------- | --------------- |
| 1    | f0/0     | 192.168.13.1   | 255.255.255.192 |
| 2    | f0/1     | 192.168.13.65  | 255.255.255.192 |
| 3    | f1/0     | 192.168.13.129 | 255.255.255.192 |



### CONFIGURACIÓN DE INTERFACES FAST ETHERNET DEL ROUTER C3725

Una vez con la topología realizada en GNS3, y con el router iniciado abrimos la terminal para empezar a configurarlo, veremos la siguiente ventana:

<img src="/SS/R1.PNG" alt="drawing" width="600"/> 

Para entrar a la configuración del router scribimos el siguiente comando:  
`conf t`  

<img src="/SS/R2.PNG" alt="drawing" width="600"/> 

Una vez adentro para configurar la interfaz FastEthernet0/0 escribimos:   
`int f0/0` 

<img src="/SS/R3.PNG" alt="drawing" width="600"/> 

Ahora asignamos una dirección ip a la interfaz y la máscara de red con el siguiente comando:  
`ip address 192.168.13.1 255.255.255.192`

<img src="/SS/R4.PNG" alt="drawing" width="600"/> 
  
Una vez asignada al ip para esta interfaz activamos la activamos con el comando:    
`no shut`  

<img src="/SS/R5.PNG" alt="drawing" width="600"/> 

Configuramos la otra interfaz que es la FastEthernet0/1 con los mismos comandos que utilizamos en la interfaz anterior, solamente aplicando cambios en el nombre de la interfaz y la dirección IP utilizando el siguiente comando:   
`int f0/1`  

<img src="/SS/R6.PNG" alt="drawing" width="600"/> 

Ahora asignamos una dirección ip a la interfaz y la máscara de red con el siguiente comando:  
`ip address 192.168.13.65 255.255.255.192`  

<img src="/SS/R7.PNG" alt="drawing" width="600"/> 
  
Una vez asignada al ip para esta interfaz activamos la activamos con el comando:  
`no shut`  

<img src="/SS/R8.PNG" alt="drawing" width="600"/> 

Configuramos la otra interfaz que es la FastEthernet1/0 con los mismos comandos que utilizamos en la interfaz anterior, solamente aplicando cambios en el nombre de la interfaz y la dirección IP utilizando el siguiente comando:   
`int f1/0`  

<img src="/SS/R9.PNG" alt="drawing" width="600"/> 

Ahora asignamos una dirección ip a la interfaz y la máscara de red con el siguiente comando:  
`ip address 192.168.13.129 255.255.255.192`  

<img src="/SS/R10.PNG" alt="drawing" width="600"/> 
  
Una vez asignada al ip para esta interfaz activamos la activamos con el comando:  
`no shut`  

<img src="/SS/R11.PNG" alt="drawing" width="600"/> 

Salimos de la configuración del router con el comando exit y escribimos el siguiente comando para ver las direcciones asignadas:  
`sh ip int brief`  

<img src="/SS/R13.PNG" alt="drawing" width="600"/> 

Por último escribimos el siguiente comando para guardar los cambios permanentemente  
`wr`  

<img src="/SS/R14.PNG" alt="drawing" width="600"/> 


### CONFIGURACIÓN DE HOST PC1
Una vez configuradas las direcciones de las interfaces del router, procedemos a encender nuestros host, en este caso la que tiene por nombre PC1, ingresando a la consola tendríamos la siguiente ventana:

<img src="/SS/PC1.PNG" alt="drawing" width="600"/> 

A continuación asignamos la IP y definimos la máscara de red y el gateway correspondiente a esta máquina con el siguiente comando:  
`ip 192.168.13.10 255.255.255.192 192.168.13.1`  

<img src="/SS/PC2.PNG" alt="drawing" width="600"/>

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando:  
`show ip`  

Por último utilizamos el siguiente comando para guardar las configuraciones realizadas  
`save`

<img src="/SS/PC3.PNG" alt="drawing" width="600"/> 

Realizamos la misma configuracion en los otros host para asignar la ip y el gateway correspondientes.  

### CONFIGURACIÓN DE HOST PC2
Una vez configuradas las direcciones de las interfaces del router, procedemos a encender nuestros host, en este caso la que tiene por nombre PC2, ingresando a la consola tendríamos la siguiente ventana:

<img src="/SS/PC4.PNG" alt="drawing" width="600"/> 

A continuación asignamos la IP y definimos la máscara de red y el gateway correspondiente a esta máquina con el siguiente comando:  
`ip 192.168.13.20 255.255.255.192 192.168.13.1`  

<img src="/SS/PC5.PNG" alt="drawing" width="600"/>

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando:  
`show ip`  

Por último utilizamos el siguiente comando para guardar las configuraciones realizadas  
`save`

<img src="/SS/PC6.PNG" alt="drawing" width="600"/> 

Realizamos la misma configuracion en los otros host para asignar la ip y el gateway correspondientes.   

### CONFIGURACIÓN DE HOST PC3
Una vez configuradas las direcciones de las interfaces del router, procedemos a encender nuestros host, en este caso la que tiene por nombre PC3, ingresando a la consola tendríamos la siguiente ventana:

<img src="/SS/PC7.PNG" alt="drawing" width="600"/> 

A continuación asignamos la IP y definimos la máscara de red y el gateway correspondiente a esta máquina con el siguiente comando:  
`ip 192.168.13.80 255.255.255.192 192.168.13.65`  

<img src="/SS/PC8.PNG" alt="drawing" width="600"/>

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando:  
`show ip`  

Por último utilizamos el siguiente comando para guardar las configuraciones realizadas  
`save`

<img src="/SS/PC9.PNG" alt="drawing" width="600"/> 

Realizamos la misma configuracion en los otros host para asignar la ip y el gateway correspondientes. 

### CONFIGURACIÓN DE HOST PC4
Una vez configuradas las direcciones de las interfaces del router, procedemos a encender nuestros host, en este caso la que tiene por nombre PC4, ingresando a la consola tendríamos la siguiente ventana:

<img src="/SS/PC10.PNG" alt="drawing" width="600"/> 

A continuación asignamos la IP y definimos la máscara de red y el gateway correspondiente a esta máquina con el siguiente comando:  
`ip 192.168.13.90 255.255.255.192 192.168.13.65`  

<img src="/SS/PC11.PNG" alt="drawing" width="600"/>

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando:  
`show ip`  

Por último utilizamos el siguiente comando para guardar las configuraciones realizadas  
`save`

<img src="/SS/PC12.PNG" alt="drawing" width="600"/> 

Realizamos la misma configuracion en los otros host para asignar la ip y el gateway correspondientes. 

### CONFIGURACIÓN DE HOST PC5
Una vez configuradas las direcciones de las interfaces del router, procedemos a encender nuestros host, en este caso la que tiene por nombre PC5, ingresando a la consola tendríamos la siguiente ventana:

<img src="/SS/PC11.PNG" alt="drawing" width="600"/> 

A continuación asignamos la IP y definimos la máscara de red y el gateway correspondiente a esta máquina con el siguiente comando:  
`ip 192.168.13.100 255.255.255.192 192.168.13.65`  

<img src="/SS/PC12.PNG" alt="drawing" width="600"/>

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando:  
`show ip`  

Por último utilizamos el siguiente comando para guardar las configuraciones realizadas  
`save`

<img src="/SS/PC13.PNG" alt="drawing" width="600"/> 

Realizamos la misma configuracion en los otros host para asignar la ip y el gateway correspondientes. 

### CONFIGURACIÓN DE HOST LINUX-1/PC6
Procedemos a encender nuestra máquina virtual y para esta práctica se utilizó TinyCore Linux, veremos una ventana en donde seleccionaremos la opción llamada **Boot TinyCore** para iniciar el sistema operativo 

<img src="/SS/L1.PNG" alt="drawing" width="600"/> 

Una vez ubicados en el escritorio, nos dirigimos a la parte inferior de esta y buscamos la opcion que se llama **Panel de Control** la cual nos permitirá acceder a las configuraciones de la máquina. Estando en el menú que nos apareció seleccionamos la opción de **Network**, para gestionar las configuraciones de red

<img src="/SS/L2.PNG" alt="drawing" width="600"/> 

En el apartado de **IP Address** escribiremos la dirección IP asignada a esta máquina la cuál es: **192.168.13.150** máscara de red **255.255.255.192** y gateway **192.168.18.192** , selecccionamos la opción de **Apply** y luego **Exit** para finalizar con la configuración

<img src="/SS/L3.PNG" alt="drawing" width="600"/> 

Para mostrar las configuraciones que hemos realizado podemos ejecutar el siguiente comando en la terminal:  
`ifconfig` 

<img src="/SS/L4.PNG" alt="drawing" width="600"/> 

## PRUEBAS DE CONFIGURACION 

Para comprobar el correcto funcionamiento de la topología realizada y verificar que las direcciones ip se hayan asignado correctamente realizaremos pruebas de comunicación entre los host configurados, para ello utilizaremos el comando **ping**


### PRUEBAS DE CONEXIÓN PC1

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC2:      **ping 192.168.13.20**
- COMUNICACIÓN CON EL HOST PC3:      **ping 192.168.13.80**
- COMUNICACIÓN CON EL HOST PC4:      **ping 192.168.13.90**
- COMUNICACIÓN CON EL HOST PC5:      **ping 192.168.18.100**
- COMUNICACIÓN CON EL HOST PC6:      **ping 192.168.13.150**

<img src="/SS/T1.PNG" alt="drawing" width="600"/> 


### PRUEBAS DE CONEXIÓN PC2

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC1:      **ping 192.168.13.10**
- COMUNICACIÓN CON EL HOST PC3:      **ping 192.168.13.80**
- COMUNICACIÓN CON EL HOST PC4:      **ping 192.168.13.90**
- COMUNICACIÓN CON EL HOST PC5:      **ping 192.168.18.100**
- COMUNICACIÓN CON EL HOST PC6:      **ping 192.168.13.150**

<img src="/SS/T2.PNG" alt="drawing" width="600"/> 

### PRUEBAS DE CONEXIÓN PC3

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC1:      **ping 192.168.13.10**
- COMUNICACIÓN CON EL HOST PC2:      **ping 192.168.13.20**
- COMUNICACIÓN CON EL HOST PC4:      **ping 192.168.13.90**
- COMUNICACIÓN CON EL HOST PC5:      **ping 192.168.18.100**
- COMUNICACIÓN CON EL HOST PC6:      **ping 192.168.13.150**

<img src="/SS/T3.PNG" alt="drawing" width="600"/> 

### PRUEBAS DE CONEXIÓN PC4

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC1:      **ping 192.168.13.10**
- COMUNICACIÓN CON EL HOST PC2:      **ping 192.168.13.20**
- COMUNICACIÓN CON EL HOST PC3:      **ping 192.168.13.80**
- COMUNICACIÓN CON EL HOST PC5:      **ping 192.168.18.100**
- COMUNICACIÓN CON EL HOST PC6:      **ping 192.168.13.150**

<img src="/SS/T4.PNG" alt="drawing" width="600"/> 

### PRUEBAS DE CONEXIÓN PC5

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC1:      **ping 192.168.13.10**
- COMUNICACIÓN CON EL HOST PC2:      **ping 192.168.13.20**
- COMUNICACIÓN CON EL HOST PC3:      **ping 192.168.13.80**
- COMUNICACIÓN CON EL HOST PC4:      **ping 192.168.18.90**
- COMUNICACIÓN CON EL HOST PC6:      **ping 192.168.13.150**

<img src="/SS/T4.PNG" alt="drawing" width="600"/> 

 
### PRUEBAS DE CONEXIÓN LINUX-1/PC6

En la consola de la máquina virtual debemos escribir los siguientes comandos:  
- COMUNICACIÓN CON EL HOST PC1:      **ping 192.168.13.10**
- COMUNICACIÓN CON EL HOST PC2:      **ping 192.168.13.20**
- COMUNICACIÓN CON EL HOST PC3:      **ping 192.168.13.80**
- COMUNICACIÓN CON EL HOST PC4:      **ping 192.168.18.90**
- COMUNICACIÓN CON EL HOST PC5:      **ping 192.168.13.100**

<img src="/SS/T6.PNG" alt="drawing" width="600"/> 

