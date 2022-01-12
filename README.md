# terraform-random
Random provider [see doc](https://registry.terraform.io/providers/hashicorp/random/latest/docs) can generate randomness that can be used in the terraform configuration, for example with tags.

Purpose of this repo is to generate a random number over 4 bytes length and view it after.
```
resource "random_id" "suffix_tags" {
  byte_length = 4
}
```

# How to use this repo
Clone
```
git clone https://github.com/ion-training/terraform-random.git
```

cd into new dir
```
cd terraform-random
```

Terraform init to pull random provider
```
terraform init
```

Create a new random
```
terraform apply -auto-approve
```

View the random generated (see hex and dec)
```
terraform show
```

# Sample Output
```
$ terraform apply -auto-approve

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # random_id.suffix_tags will be created
  + resource "random_id" "suffix_tags" {
      + b64_std     = (known after apply)
      + b64_url     = (known after apply)
      + byte_length = 4
      + dec         = (known after apply)
      + hex         = (known after apply)
      + id          = (known after apply)
    }

Plan: 1 to add, 0 to change, 0 to destroy.
random_id.suffix_tags: Creating...
random_id.suffix_tags: Creation complete after 1s [id=KMOrsw]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
```

```
$ terraform show
# random_id.suffix_tags:
resource "random_id" "suffix_tags" {
    b64_std     = "KMOrsw=="
    b64_url     = "KMOrsw"
    byte_length = 4
    dec         = "683912115"
    hex         = "28c3abb3"
    id          = "KMOrsw"
}
```

```
$ terraform destroy -auto-approve
random_id.suffix_tags: Refreshing state... [id=KMOrsw]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # random_id.suffix_tags will be destroyed
  - resource "random_id" "suffix_tags" {
      - b64_std     = "KMOrsw==" -> null
      - b64_url     = "KMOrsw" -> null
      - byte_length = 4 -> null
      - dec         = "683912115" -> null
      - hex         = "28c3abb3" -> null
      - id          = "KMOrsw" -> null
    }

Plan: 0 to add, 0 to change, 1 to destroy.
random_id.suffix_tags: Destroying... [id=KMOrsw]
random_id.suffix_tags: Destruction complete after 0s

Destroy complete! Resources: 1 destroyed.
$
```
