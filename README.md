# GitHub Action: Upload Log to S3

Esta acción de GitHub permite subir un archivo de log en formato `.txt` a un bucket de Amazon S3.

## Variables de Entrada

- `log-text`: El texto que se incluirá dentro del archivo `.txt`.
- `aws-access-key-id`: La clave de acceso de AWS.
- `aws-secret-access-key`: La clave secreta de acceso de AWS.
- `bucket-name`: El nombre del bucket de S3 donde se subirá el archivo.

## Uso

```yaml
name: Upload Log to S3

on: [push]

jobs:
    upload-log:
        runs-on: ubuntu-latest
        steps:
            - name: Checkout code
                uses: actions/checkout@v2

            - name: Upload log to S3
                uses: ./path/to/your/action
                with:
                    log_text: "Este es el contenido del log."
                    aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
                    aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
                    bucket_name: "nombre-del-bucket"
```

## Ejemplo de Archivo de Configuración

```yaml
name: CI

on: [push]

jobs:
    build:
        runs-on: ubuntu-latest

        steps:
        - name: Checkout code
            uses: actions/checkout@v2

        - name: Upload log to S3
            uses: ./upload-log-s3
            with:
                log_text: "Build completed successfully."
                aws_access_key_id: ${{ secrets.AWS_ACCESS_KEY_ID }}
                aws_secret_access_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
                bucket_name: "my-s3-bucket"
```

## Licencia

Este proyecto está licenciado bajo los términos de la licencia MIT.