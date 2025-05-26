# Desafio3

## Requisito 1: Crear bucket.
```bash
aws s3 mb s3://bucket-desafio-jsa
```
respuesta:
make_bucket: bucket-desafio-jsa

## Requisito 2: Crear rol con politica de escritura sobre el bucket.
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
