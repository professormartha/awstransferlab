A continuación, va a crear dos políticas de IAM. La primera política se va a aplicar a un rol de IAM y va a permitir al servicio de AWS Transfer for SFTP interactuar con el servicio de S3 y en específico con el bucket que creó en el primer módulo. La segunda política va a permitir que los usuarios del servicio de AWS Transfer for SFTP únicamente puedan acceder al folder que lleva su nombre dentro del bucket de S3.

1. Haga click en Services y posteriormente seleccione el servicio de IAM (https://console.aws.amazon.com/iam/) que se encuentra bajo la categoría de Security, Identity & Compliance (también puede teclear IAM en el campo de búsqueda).
2. Haga click en Policies en el menú del lado izquierdo.
3. Haga click en Create policy.
4. En la siguiente pantalla haga click en la pestaña de JSON, borre el contenido existente en el campo y pegue la siguiente política sustituyendo las dos entradas de bucket_name por el nombre del bucket que acaba de crear:

> {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowListingOfUserFolder",
            "Action": [
                "s3:ListBucket",
                "s3:GetBucketLocation"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::bucket_name"
            ]
        },
        {
            "Sid": "HomeDirObjectAccess",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:DeleteObjectVersion",
                "s3:DeleteObject",
                "s3:GetObjectVersion"
            ],
            "Resource": "arn:aws:s3:::bucket_name/*"
        }
    ]
>}

