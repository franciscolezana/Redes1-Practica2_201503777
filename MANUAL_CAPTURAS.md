<img src="https://portal.ingenieria.usac.edu.gt/images/2019/logo/logo-fiusac.png"/>



**NOMBRE**: FRANCISCO HUMBERTO LEZANA RAMOS  
**CARNET**: 201503777  
**CURSO**: REDES DE COMPUTADORAS 1

# MANUAL DE CONFIGURACIÓN PARA CAPTURAS DE PAQUETES Y CÁLCULO DE DOMINIOS DE BROADCAST Y DOMINIOS DE COLISIÓN 

## HERRAMIENTAS A UTILIZAR 

- GNS3
- Software de virtualización (VMWare o Virtual Box) instalados y configurado para uso con GNS3.
- Wireshark 

## TOPOLOGIA DE RED DEL PROYECTO 

La siguiente topología cuenta con 6 host de los cuales 5 son VPCS y 1 es una máquina virtual con un sistema tiny-linux para ahorrar recursos, podemos observar que los host se conectan a 3 switches distintos los cuales representan a los distintos departamentos de la empresa ( finanzas, ventas e informática) y estos se conectan entre sí por medio de un router el cuál será centro principal de comunicación.
<img src="/SS/TOPO.PNG"/>


## CALCULOS DE DOMINIO DE BROADCAST Y DOMINIOS DE COLISIÓN DE LA TOPOLOGÍA IMPLEMENTADA

# Dominios de Colisión y de Broadcast
Para calcular los dominios utilizaremos la siguiente tabla:

| DISPOSITIVO | NO. DOMINIOS DE BROADCAST | NO. DOMINIOS DE COLISIÓN                                     |
| ----------- | ------------------------- | ------------------------------------------------------------ |
| SWITCH      | 1 Dominio de broadcast    | n Dominios de colisión          (n = #de puertos encendidos) |
| ROUTER      | 1 Dominio de broadcast    | 1 Dominio de Colisión                                        |


Como podemos ver el router cuenta con 1 dominio de colisión y 1 de broadcast por cada interfaz, en este caso, contamos con 3 interfaces, 1 por cada switch, por tanto:
### DC = 3  
### DB = 3

En cuanto a los switch, estos representan 6 dominios de colisión ( 1 por cada dispositivo conectado ) , cada uno va hacia una VPC o la virtual por lo que en total tendríamos.
### DC = 9   
### DB = 3

El cálculo representado en la topología quedará de la siguiente forma: 

<img src="/SS/TOPO2.PNG"> 


## CAPTURA DE PAQUETES

Para realizar la captura de paquetes debemos de dar click derecho en cualquier conexión entre de nuestra topología y seleccionar **Start Capture** lo cual abrirá el programa wireshark para observar la captura de paquetes
, luego de esto nos basta con utilizar el comando **ping** para observar como los paquetes son interceptados por el programa.

<img src="/SS/Captura0.PNG" alt="drawing" width="600"/>

## CAPTURA DE PAQUETES PC1

<img src="/SS/Captura1.PNG" alt="drawing" width="600"/>


## CAPTURA DE PAQUETES PC2

<img src="/SS/Captura2.PNG" alt="drawing" width="600"/>


## CAPTURA DE PAQUETES PC3

<img src="/SS/Captura3.PNG" alt="drawing" width="600"/>


## CAPTURA DE PAQUETES PC4

<img src="/SS/Captura4.PNG" alt="drawing" width="600"/>


## CAPTURA DE PAQUETES PC5

<img src="/SS/Captura5.PNG" alt="drawing" width="600"/>


## CAPTURA DE PAQUETES PC6

<img src="/SS/Captura6.PNG" alt="drawing" width="600"/>

