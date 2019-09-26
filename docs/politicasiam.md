A continuación, va a crear dos políticas de IAM. La primera política se va a aplicar a un rol de IAM y va a permitir al servicio de AWS Transfer for SFTP interactuar con el servicio de S3 y en específico con el bucket que creó en el primer módulo. La segunda política va a permitir que los usuarios del servicio de AWS Transfer for SFTP únicamente puedan acceder al folder que lleva su nombre dentro del bucket de S3.

1. Haga click en **_Services_** y posteriormente seleccione el servicio de **_IAM_** (**_https://console.aws.amazon.com/iam/_**) que se encuentra bajo la categoría de **_Security, Identity & Compliance_** (también puede teclear IAM en el campo de búsqueda).
2. Haga click en **_Policies_** en el menú del lado izquierdo.
3. Haga click en **_Create policy_**.
4. En la siguiente pantalla haga click en la pestaña de **_JSON_**, borre el contenido existente en el campo y pegue la siguiente política sustituyendo las dos entradas de **_bucket_name_** por el nombre del bucket que acaba de creó en el módulo anterior:

 {
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
                "arn:aws:s3:::**_bucket_name_**"
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
            "Resource": "arn:aws:s3:::**_bucket_name_**/*"
        }
    ]
}

5.	Haga click el botón de **_Review policy_**.
6.	Ingrese un nombre para la política (**_AWSTransferCustomPolicy_**) en el campo de **_Name_**.
7.	Haga click en **_Create policy_**.
8.	Haga click de nuevo en **_Policies_** en el menú del lado izquierdo.
9.	Haga click en **_Create policy_**.
10.	En la siguiente pantalla haga click en la pestaña de **_JSON_**, borre el contenido existente en el campo y pegue la siguiente política:

{
  "Version": "2012-10-17",
  "Statement": [
      {
          "Sid": "AllowListingOfUserFolder",
          "Action": [
              "s3:ListBucket"
          ],
          "Effect": "Allow",
          "Resource": [
              "arn:aws:s3:::${transfer:HomeBucket}"
          ],
          "Condition": {
              "StringLike": {
                  "s3:prefix": [
                      "${transfer:HomeFolder}/*",
                      "${transfer:HomeFolder}"
                  ]
              }
          }
      },
      {
          "Sid": "HomeDirObjectAccess",
          "Effect": "Allow",
          "Action": [
              "s3:PutObject",
              "s3:GetObject",
              "s3:DeleteObjectVersion",
              "s3:DeleteObject",
              "s3:GetObjectVersion",
              "s3:GetObjectACL",
              "s3:PutObjectACL"
          ],
          "Resource": "arn:aws:s3:::${transfer:HomeDirectory}*"
       }
  ]
}

11.	Haga click el botón de **_Review policy_**.
12.	Ingrese un nombre para la política (**_AWSTransferScopeDownPolicy_**) en el campo de **_Name_**.
13.	Haga click en **_Create policy_**.

