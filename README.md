# Desafio3

## Requisito 1: Crear bucket.
```bash
aws s3 mb s3://bucket-desafio-jsa
```
respuesta:
make_bucket: bucket-desafio-jsa

## Requisito 2: Crear rol con politica de escritura sobre el bucket.
Primero creamos el usuario:
```bash
aws iam create-user --user-name s3-support
```
Primero se define la politica en json que permite escribir en el bucket:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::bucket-desafio-jsa/*"
    }
  ]
}
```
Segundo creamos el rol que podra ser asumido por el usuario para obtener permisos de escritura en el bucket:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::000000000000:user/s3-support"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
