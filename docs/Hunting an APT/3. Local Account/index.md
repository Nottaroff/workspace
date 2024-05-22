---
title:  Local Account 👤
layout: default
has_toc: false
nav_order: 3
parent: Hunting an APT 👺
---

# Hunting an APT - **Local Account** 


{: .intro }
>Es posible mantener la persistencia una vez que el adversario entre en nuestro sistema mediante la creacion cuentas de usuario.

<body>
    <div style="display: flex; align-items: center;">
        <div style="flex: 1;">
            <p>Vamos a ver un ejemplo de detección de creación de cuentas de usuario sospechosas. Las cuentas locales son aquellas configuradas por una organización para su uso por usuarios, soporte remoto, servicios o para la administración en un único sistema o servicio. Con un nivel de acceso suficiente, se puede utilizar el comando net user /add para crear una cuenta local.</p>
        </div>
        <div style="flex: 1;">
            <img src="https://i.postimg.cc/zDwhYVJn/LOAC1.png" alt="LOAC1" style="width:100%;">
        </div>
    </div>
</body>

Inicio
Código de evento de Windows para la creación de cuentas:
ID de evento del registro de seguridad de Windows 4720
Podemos buscar el evento 4720 en nuestros sistemas con Splunk:

`index=botsv2 sourcetype="¡wineventlog EventCode=4720`

![LOAC2.png](https://i.postimg.cc/8Ptrs9fc/LOAC2.png)



Aquí tenemos 4 eventos de creación de cuentas de usuario.
Analizando los campos clave del nombre de la cuenta:

![LOAC3.png](https://i.postimg.cc/8cGrrVbJ/LOAC3.png) 



svcnc se menciona 4 veces y se crearon las cuentas service3 y billy.tun.
Revisando dónde y cuándo se crearon las cuentas.

`index=botsv2 sourcetype=wineventlog EventCode=4720 Account_Name=svcvnc
| table _time host Account_Name SAM_Account_Name`

![LOAC4.png](https://i.postimg.cc/xCMzCdLV/LOAC4.png)

Podemos ver la hora y en qué sistema ocurrieron los eventos. Los registros de creación de eventos ocurrieron en dos estaciones de trabajo y dos servidores. Parece que en la estación de trabajo "billy" fue la primera en la que se añadió un usuario y la cuenta "service3" se utilizó en los sistemas restantes.
La creación de la misma cuenta en cuatro sistemas diferentes en un corto período de tiempo es sospechosa. Para analizarlo más a fondo, podemos tomar los valores de los atributos en el registro de eventos de Windows y usar los comandos table y transpose para comparar los valores en todos los sistemas.
Podemos ver que estos campos adicionales están consistentemente vacíos en todos los sistemas. Es extraño que estos atributos no estén establecidos.

`index=botsv2 sourcetype=wineventlog EventCode=4720 Account_Name=svcvnc
| table _time host Account_Name SAM_Account_Name Display_Name User_Principal_Name Home_Directory Home_Drive Script_Path Profile_Path User_Workstations Password_Last_Set Account_Expires Logon_Hours
|transpose`

![LOAC5.png](https://i.postimg.cc/QMR7h79q/LOAC5.png)

Códigos de Evento Adicionales
Para complementar el análisis de la creación de cuentas sospechosas, podemos revisar otros eventos que ocurrieron en el mismo período de tiempo. Primero, ajustaremos el rango de tiempo entre la primera y la última creación de cuenta. Luego, revisaremos todos los códigos de eventos que ocurrieron durante este tiempo.
Además del código de evento 4720 para la creación de cuentas, hay otros códigos de eventos de seguridad en Windows que pueden ser útiles para el análisis y monitoreo de actividades sospechosas relacionadas con las cuentas de usuario:

- 4722: Una cuenta de usuario fue habilitada.
- 4723: Un intento de cambiar la contraseña de una cuenta de usuario.
- 4724: Un intento de restablecer la contraseña de una cuenta de usuario.
- 4725: Una cuenta de usuario fue deshabilitada.
- 4726: Una cuenta de usuario fue eliminada.
- 4738: Una cuenta de usuario fue modificada.
- 4740: Una cuenta de usuario fue bloqueada.
- 4767: Una cuenta de usuario fue desbloqueada.

`index=botsv2 sourcetype=wineventlog (host="wrk-klagerf" OR host="wrk-btun" ) EventCode!=4688
| eval current_accont=mvindex(Security_ID,0)
| eval account_modified=mvindex(Security_ID,1)
| rex field=Message "(?<short_message>.*\r)"
| table _time host EventCode current_account account_modified Security_ID short_message
| sort _time`


Por ejemplo, los códigos de eventos 4738 y 4732 pueden indicar que un usuario fue añadido al grupo de seguridad global o al grupo

![LOAC6.png](https://i.postimg.cc/Fs9LrNRw/LOAC6.png)

Eventos de Credenciales Explícitas
El evento 4648 es un intento de inicio de sesión de usuario. Podemos observar cómo se utiliza la cuenta para iniciar sesión en otros sistemas.

## Conlusión
La cuenta de usuario svcvnc fue creada en cuatro sistemas:
- 2 servidores (mercury y venus)
- 2 estaciones de trabajo (wrk-btun y wrk-klagerf)

Todas las cuentas fueron creadas dentro de una ventana de 40 minutos el 23 de agosto.
Se insertó un mínimo de información en la cuenta de usuario al momento de la creación.
Tres cuentas fueron creadas por la cuenta service3.

La primera cuenta fue creada por la cuenta billy.tun.

La creación de múltiples cuentas de usuario en varios sistemas en un corto período de tiempo, junto con la falta de información detallada en las cuentas, nos indica un intento de acceso no autorizado.

![LOAC8.png](https://i.postimg.cc/zvkHCPdd/LOAC8.png)