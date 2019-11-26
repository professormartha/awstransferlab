1. Diríjase de nuevo servicio de [**_AWS Transfer for SFTP_**](https://console.aws.amazon.com/transfer/)
2. Seleccione el servidor que creó anteriormente y haga click en **_Add user_**.
3. En el campo de **_Username_** escriba **_user01_**.
4. En **_Access_** seleccione el rol que creó (**_AWSTransferCustomRole_**) del menú desplegable.
5. En **_Policy_** seleccione **_Select policy from IAM_** y del menu desplegable seleccione la segunda política que creó (**_AWSTransferScopeDownPolicy_**).
6. En **_Home directory_** seleccione el bucket que creó (**_transfer-lab-su-nombre_**).
7. En el campo de **_Enter optional folder_** escriba **_user01_** (que es el nombre del usuario que está creando y del folder que creó dentro del bucket de S3).
8. En el campo de **_SSH public key_** debe ingresar una llave pública generada por usted.  Si usted es usuario de **_Windows_** puede aprender como generar llaves con [**_puttygen_**](https://www.ssh.com/ssh/putty/windows/puttygen). Si usted es usuario de **_Linux/Mac_**, ejecute el siguiente comando en terminal sustituyendo **_key_name_** por el nombre que guste dar a su llave (puede ser el nombre del usuario que está creando):

```
ssh-keygen -P "" -f key_name
```

9. Ejecute el siguiente comando sustituyendo **_key_name_** por el nombnre que dio a su llave:

```
cat key_name.pub
```

Deberá ver algo así:
> ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDEk7oaoFk947Zaq2lfZbWsLBfW874+hn8ZPFIt+s3Zt
5tOW72ZocCbuq6KsyzS4AMCSfeKEEVMWaTpm5oZaFbcTJRfDF55DvsV2gezJwH1l5pWMRjqt
Q9BeH6V7sxrelU66YL4CvollCt23WfIV8rJybfrr7zsPglMVZSGxfhHA88Oi9s3XYqfZx7w4
edAkG9+WtiEx3bmPDTt1FaZlB+L9cUCEBnn3af39RR9EfbKzRAtLQ7W8t3uFlg5wG92fKcVQ
bl4BOBvOuox+M81tuxhGSonRrO/7pwRYLncYoscF7nT7yaN/7yrJtWFr3jWN7M9tFP8Hg3ZI
x1tU5h9kN+v user@system

10. Copie todo el resultado del comando anterior desde **_ssh-rsa_** hasta el último caracter antes de **_user@system_** e ingréselo n el campo de **_SSH public key_**.

Al final, la pantalla de creación de usuario debe verse así:

![Create S3 bucket](images/usercreation.png)

11. Haga click en **_Add_**.
12. **_Opcional:_** repita los pasos a de este módulo para crear un segundo usuario (**_user02_**).
