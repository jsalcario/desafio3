# Desafio3
## Paso 1: Crear bucket
```aws s3 mb s3://bucket-desafio-jsa```
### respuesta:
### make_bucket: bucket-desafio-jsa
## Paso 2: Crear usuario
```aws iam create-user --user-name s3-support```
### respuesta:
```
{
    "User": {
        "Path": "/",
        "UserName": "s3-support",
        "UserId": "AIDAU6GD3XJVRPJZPHXT2",
        "Arn": "arn:aws:iam::339713178219:user/s3-support",
        "CreateDate": "2025-05-25T20:14:55+00:00"
    }
}
```
## Paso 2: Crear rol
## Crear archivo con politicas de escritura en el bucket
[s3_write_policy](src/components/s3_write_policy.json)
