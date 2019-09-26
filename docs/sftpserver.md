1. Diríjase al servicio de AWS Transfer for SFTP localizado en:
https://console.aws.amazon.com/transfer/
2. Haga click en Create server.
3. En Endpoint type seleccione Public.
4. En Identity provider seleccione Service managed.
5. Haga click en Create server.
6. En la siguiente pantalla verá como su servidor se está iniciando (State = Starting). 
7. Haga click en el valor de Server ID.

![Create S3 bucket](images/serverid.png)

8. Copie el valor de Endpoint (algo así como s-0ba49c574e034074a.server.transfer.us-east-1.amazonaws.com) y guárdelo en un editor de texto ya que lo necesitará más tarde para conectarse a su servidor SFTP.