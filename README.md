
# Laboratorio 11 — Infrastructure as Code con Terraform y Floci

Implementamos una plataforma local de Big Data utilizando Terraform como herramienta de infraestructura como código y Floci como emulador de servicios AWS.

## Tecnologías

- Terraform
- Docker Compose
- Floci
- AWS CLI
- Amazon S3
- AWS Glue Data Catalog

## Arquitectura

La plataforma utiliza el bucket `ucv-data-platform`, organizado en cuatro dominios:

- sales
- customers
- products
- marketing

Cada dominio cuenta con tres capas de almacenamiento: Bronze, Silver y Gold.

También implementamos una base de datos Glue por dominio.

## Ejecución

Iniciar Floci:

```bash
docker compose up -d
```

Inicializar y aprovisionar la infraestructura:

```bash
cd terraform
terraform init
terraform validate
terraform plan
terraform apply
```

Verificar los recursos:

```bash
aws --endpoint-url http://localhost:4566 s3 ls
aws --endpoint-url http://localhost:4566 glue get-databases
```

Eliminar los recursos administrados:

```bash
terraform destroy
```

## Resultado

Aprovisionamos 17 recursos: un bucket S3, doce prefijos de almacenamiento y cuatro bases de datos Glue.
