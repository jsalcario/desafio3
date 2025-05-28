# Desafio3

## Requisito 1: Crear bucket.
```bash
aws s3 mb s3://bucket-desafio3-jsa
```
respuesta:
make_bucket: bucket-desafio-jsa

## Requisito 2: Crear rol con politica de escritura sobre el bucket.
Creamos el usuario s3-support solicitado:
```bash
aws iam create-user --user-name s3-support
```
Se define la politica en json que permite escribir en el bucket y lo guardamos con el nombre `s3_write_policy.json`:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::bucket-desafio3-jsa/*"
    }
  ]
}
```
Creamos el rol que podra ser asumido por el usuario para obtener permisos de escritura en el bucket y lo guardamos con el nombre `trust_policy.json`:
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
Creamos la politica:
```bash
aws iam create-policy --policy-name S3WritePolicy --policy-document file://s3_write_policy.json
```
Siguiente creamos el rol:
```bash
aws iam create-role --role-name S3WriteRole --assume-role-policy-document file://trust_policy.json
```
