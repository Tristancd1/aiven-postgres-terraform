# aiven-postgres-terraform
Terraform script to create a simple postgres cluster on the Aiven platform

## What it creates

- An Aiven for PostgreSQL service (`business-4` plan on `google-us-east1`) in an existing Aiven project
- An output, `pg_service_uri`, with the service's connection URI

## Prerequisites

- [Terraform](https://developer.hashicorp.com/terraform/install) 0.13 or later
- An Aiven account with a project that is assigned to a billing group
- An Aiven [personal token](https://aiven.io/docs/platform/howto/create_authentication_token)

## Configure

Copy the example variables file and fill in your values:

```bash
cp terraform.tfvars.example terraform.tfvars
```

| Variable                | Description                          | Default                 |
|-------------------------|--------------------------------------|-------------------------|
| `aiven_token`           | Aiven personal token                 | (required)              |
| `aiven_project_name`    | Name of your existing Aiven project  | (required)              |
| `postgres_service_name` | Name of the PostgreSQL service       | `example-us-pg-service` |

## Run

Download the Aiven provider:

```bash
terraform init
```

Preview the changes:

```bash
terraform plan
```

Create the service (it takes a few minutes to start):

```bash
terraform apply
```

You should now be able to see the service building in the Aiven console.