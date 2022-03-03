# tf-for-each

# Repository for learning Terraform OSS
This repository has been created only for learning purposes to try the `for_each` meta-argument in Terraform OSS

### Prerequisites

- [X] [Terraform](https://www.terraform.io/downloads)
- [X] [AWS Account](https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Fportal.aws.amazon.com%2Fbilling%2Fsignup%2Fresume&client_id=signup&code_challenge_method=SHA-256&code_challenge=goaHJzR6L_4316BbJ-3mYe5YqoOcQY7fKzTaPrN2SyA)

## How to Use this Repo

- Clone this repository:
```shell
git clone git@github.com:dlavric/tf-for-each.git
```

- Go to the directory where the repo is stored:
```shell
cd tf-for-each
```

- Export your AWS credentials in your terminal:
```shell
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export AWS_SESSION_TOKEN=...
```


- Run `terraform init`, to download any external dependency
```shell
terraform init
```


This is the output of initializing the Terraform code:
```shell
Initializing the backend...

Initializing provider plugins...
- Finding hashicorp/aws versions matching "4.3.0"...
- Installing hashicorp/aws v4.3.0...
- Installed hashicorp/aws v4.3.0 (self-signed, key ID 34365D9472D7468F)

Partner and community providers are signed by their developers.
If you'd like to know more about provider signing, you can read about it here:
https://www.terraform.io/docs/plugins/signing.html

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

- Apply the changes with Terraform
```shell
terraform apply
```

This is the output for applying the changes:
```shell
An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_iam_user.the-accounts["Alice"] will be created
  + resource "aws_iam_user" "the-accounts" {
      + arn           = (known after apply)
      + force_destroy = false
      + id            = (known after apply)
      + name          = "Alice"
      + path          = "/"
      + tags_all      = (known after apply)
      + unique_id     = (known after apply)
    }

  # aws_iam_user.the-accounts["Dottie"] will be created
  + resource "aws_iam_user" "the-accounts" {
      + arn           = (known after apply)
      + force_destroy = false
      + id            = (known after apply)
      + name          = "Dottie"
      + path          = "/"
      + tags_all      = (known after apply)
      + unique_id     = (known after apply)
    }

  # aws_iam_user.the-accounts["James"] will be created
  + resource "aws_iam_user" "the-accounts" {
      + arn           = (known after apply)
      + force_destroy = false
      + id            = (known after apply)
      + name          = "James"
      + path          = "/"
      + tags_all      = (known after apply)
      + unique_id     = (known after apply)
    }

  # aws_iam_user.the-accounts["Todd"] will be created
  + resource "aws_iam_user" "the-accounts" {
      + arn           = (known after apply)
      + force_destroy = false
      + id            = (known after apply)
      + name          = "Todd"
      + path          = "/"
      + tags_all      = (known after apply)
      + unique_id     = (known after apply)
    }

Plan: 4 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_iam_user.the-accounts["Dottie"]: Creating...
aws_iam_user.the-accounts["Todd"]: Creating...
aws_iam_user.the-accounts["James"]: Creating...
aws_iam_user.the-accounts["Alice"]: Creating...
aws_iam_user.the-accounts["Todd"]: Creation complete after 1s [id=Todd]
aws_iam_user.the-accounts["Alice"]: Creation complete after 1s [id=Alice]
aws_iam_user.the-accounts["James"]: Creation complete after 1s [id=James]
aws_iam_user.the-accounts["Dottie"]: Creation complete after 1s [id=Dottie]

Apply complete! Resources: 4 added, 0 changed, 0 destroyed.
```

- Destroy the resources 
```shell
terraform destroy

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # aws_iam_user.the-accounts["Alice"] will be destroyed
  - resource "aws_iam_user" "the-accounts" {
      - arn           = "arn:aws:iam::938620692197:user/Alice" -> null
      - force_destroy = false -> null
      - id            = "Alice" -> null
      - name          = "Alice" -> null
      - path          = "/" -> null
      - tags_all      = {} -> null
      - unique_id     = " " -> null
    }

  # aws_iam_user.the-accounts["Dottie"] will be destroyed
  - resource "aws_iam_user" "the-accounts" {
      - arn           = "arn:aws:iam::938620692197:user/Dottie" -> null
      - force_destroy = false -> null
      - id            = "Dottie" -> null
      - name          = "Dottie" -> null
      - path          = "/" -> null
      - tags_all      = {} -> null
      - unique_id     = " " -> null
    }

  # aws_iam_user.the-accounts["James"] will be destroyed
  - resource "aws_iam_user" "the-accounts" {
      - arn           = "arn:aws:iam::938620692197:user/James" -> null
      - force_destroy = false -> null
      - id            = "James" -> null
      - name          = "James" -> null
      - path          = "/" -> null
      - tags_all      = {} -> null
      - unique_id     = " " -> null
    }

  # aws_iam_user.the-accounts["Todd"] will be destroyed
  - resource "aws_iam_user" "the-accounts" {
      - arn           = "arn:aws:iam::938620692197:user/Todd" -> null
      - force_destroy = false -> null
      - id            = "Todd" -> null
      - name          = "Todd" -> null
      - path          = "/" -> null
      - tags_all      = {} -> null
      - unique_id     = " " -> null
    }

Plan: 0 to add, 0 to change, 4 to destroy.

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value: yes

aws_iam_user.the-accounts["Alice"]: Destroying... [id=Alice]
aws_iam_user.the-accounts["Todd"]: Destroying... [id=Todd]
aws_iam_user.the-accounts["James"]: Destroying... [id=James]
aws_iam_user.the-accounts["Dottie"]: Destroying... [id=Dottie]
aws_iam_user.the-accounts["Todd"]: Destruction complete after 0s
aws_iam_user.the-accounts["Alice"]: Destruction complete after 0s
aws_iam_user.the-accounts["Dottie"]: Destruction complete after 0s
aws_iam_user.the-accounts["James"]: Destruction complete after 0s

Destroy complete! Resources: 4 destroyed.
```

## Reference Documentation

- [Terraform for_each meta-argument](https://www.terraform.io/language/meta-arguments/for_each)

- [AWS Account and Access Keys](https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html)
