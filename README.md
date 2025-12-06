# Terraform-aws-acm

# AWS Infrastructure Provisioning with Terraform

<p align="center">
  <img src="https://img.shields.io/badge/Terraform-Module-6610f2?style=for-the-badge&logo=terraform&logoColor=white"/>
  <img src="https://img.shields.io/github/stars/yrahul05/terraform-aws-acm?style=for-the-badge"/>
</p>


> A clean and opinionated Terraform module by **[Rahul Yadav](https://github.com/yrahul05)**  
> To use this module, include it in your Terraform configuration file and provide the required input variables. Below is an example of how to use the module:
---

👤 ABOUT ME

Rahul Yadav  
Certified Cloud & DevOps Engineer  


## 🔗 Links

### Personal Profiles
> **GitHub:** [https://github.com/yrahul05](https://github.com/yrahul05)  
> **LinkedIn:** [https://www.linkedin.com/in/rahulyadavdevops/](https://www.linkedin.com/in/rahulyadavdevops/)  
> **Upwork:** [https://www.upwork.com/freelancers/~0183ad8a41e8284283](https://www.upwork.com/freelancers/~0183ad8a41e8284283)


## Examples

## Example: generate-certificate-dns

```hcl
module "acm" {
  source                    = "git::https://github.com/yrahul05/terraform-aws-acm.git?ref=v1.0.0"
  name                      = "certificate"
  environment               = "test"
  domain_name               = "example.com"
  subject_alternative_names = ["*.${local.domain}", "www.${local.domain}"]
}
```

## Example: generate-certificate-email
```hcl
module "acm" {
  source                    = "git::https://github.com/yrahul05/terraform-aws-acm.git?ref=v1.0.0"
  name                      = "certificate"
  environment               = "test"
  validate_certificate      = false
  domain_name               = "example.com"
  subject_alternative_names = ["www.example.com"]
  validation_method         = "EMAIL"
}
```

## Example: import-certificate
```hcl
module "acm" {
  source             = "git::https://github.com/yrahul05/terraform-aws-acm.git?ref=v1.0.0"
  name               = "certificate"
  environment        = "test"
  import_certificate = true
  private_key        = "./../../../yrahul05-private-key.pem"
  certificate_body   = "./../../../yrahul05-cert.pem"
  certificate_chain  = "./../../../yrahul05-chain.crt"
}
```

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.5.4 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 5.10 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 5.10 |

## Modules

| Name | Source                                                       | Version |
|------|--------------------------------------------------------------|---------|
| <a name="module_labels"></a> [labels](#module\_labels) | git::git@github.com:yrahul05/terraform-multicloud-labels.git | v1.0.0 |

## Resources

| Name | Type |
|------|------|
| [aws_acm_certificate.cert](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate) | resource |
| [aws_acm_certificate.import-cert](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate) | resource |
| [aws_acm_certificate_validation.cert](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate_validation) | resource |
| [aws_acm_certificate_validation.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/acm_certificate_validation) | resource |
| [aws_route53_record.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_zone.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/route53_zone) | data source |

## Inputs

| Name | Description                                                                                                                                                                                                                | Type | Default | Required |
|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|---------|:--------:|
| <a name="input_allow_overwrite"></a> [allow\_overwrite](#input\_allow\_overwrite) | Whether to allow overwrite of Route53 records                                                                                                                                                                              | `bool` | `true` | no |
| <a name="input_certificate_body"></a> [certificate\_body](#input\_certificate\_body) | Path of certificate body.                                                                                                                                                                                                  | `string` | `"~"` | no |
| <a name="input_certificate_chain"></a> [certificate\_chain](#input\_certificate\_chain) | Path of certificate chain.                                                                                                                                                                                                 | `string` | `""` | no |
| <a name="input_domain_name"></a> [domain\_name](#input\_domain\_name) | A domain name for which the certificate should be issued.                                                                                                                                                                  | `string` | `""` | no |
| <a name="input_enable"></a> [enable](#input\_enable) | Whether or not to enable the entire module or not.                                                                                                                                                                         | `bool` | `true` | no |
| <a name="input_enable_aws_certificate"></a> [enable\_aws\_certificate](#input\_enable\_aws\_certificate) | Set to false to prevent the creation of a acm certificate.                                                                                                                                                                 | `bool` | `true` | no |
| <a name="input_enable_dns_validation"></a> [enable\_dns\_validation](#input\_enable\_dns\_validation) | Set to prevent validation of DNS.                                                                                                                                                                                          | `bool` | `false` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Environment (e.g. `prod`, `dev`, `staging`).                                                                                                                                                                               | `string` | `""` | no |
| <a name="input_import_certificate"></a> [import\_certificate](#input\_import\_certificate) | Set to true or false to decide the creation and import of a acm certificate.                                                                                                                                               | `bool` | `false` | no |
| <a name="input_label_order"></a> [label\_order](#input\_label\_order) | Label order, e.g. `name`,`application`.                                                                                                                                                                                    | `list(any)` | <pre>[<br>  "name",<br>  "environment"<br>]</pre> | no |
| <a name="input_managedby"></a> [managedby](#input\_managedby) | ManagedBy, eg 'Rahul Yadav'                                                                                                                                                                                                | `string` | `""` | no |
| <a name="input_name"></a> [name](#input\_name) | Name  (e.g. `app` or `cluster`).                                                                                                                                                                                           | `string` | `""` | no |
| <a name="input_private_key"></a> [private\_key](#input\_private\_key) | Path of private key.                                                                                                                                                                                                       | `string` | `""` | no |
| <a name="input_private_zone"></a> [private\_zone](#input\_private\_zone) | Used with name field to get a private Hosted Zone.                                                                                                                                                                         | `bool` | `false` | no |
| <a name="input_repository"></a> [repository](#input\_repository) | Terraform current module repo                                                                                                                                                                                              | `string` | `""` | no |
| <a name="input_subject_alternative_names"></a> [subject\_alternative\_names](#input\_subject\_alternative\_names) | Set of domains that should be SANs in the issued certificate. To remove all elements of a previously configured list, set this value equal to an empty list ([]) or use the terraform taint command to trigger recreation. | `list(any)` | `[]` | no |
| <a name="input_ttl"></a> [ttl](#input\_ttl) | Time to live.                                                                                                                                                                                                              | `number` | `600` | no |
| <a name="input_validate_certificate"></a> [validate\_certificate](#input\_validate\_certificate) | Set to false to prevent the validation of a acm certificate.                                                                                                                                                               | `bool` | `false` | no |
| <a name="input_validation_method"></a> [validation\_method](#input\_validation\_method) | Which method to use for validation, DNS or EMAIL.                                                                                                                                                                          | `string` | `"DNS"` | no |
| <a name="input_validation_option"></a> [validation\_option](#input\_validation\_option) | The domain name that you want ACM to use to send you validation emails. This domain name is the suffix of the email addresses that you want ACM to use.                                                                    | `any` | `{}` | no |
| <a name="input_validation_record_fqdns"></a> [validation\_record\_fqdns](#input\_validation\_record\_fqdns) | When validation is set to DNS and the DNS validation records are set externally, provide the fqdns for the validation                                                                                                      | `list(string)` | `[]` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_acm_certificate_domain_validation_options"></a> [acm\_certificate\_domain\_validation\_options](#output\_acm\_certificate\_domain\_validation\_options) | A list of attributes to feed into other resources to complete certificate validation. Can have more than one element, e.g. if SANs are defined. Only set if DNS-validation was used. |
| <a name="output_acm_certificate_status"></a> [acm\_certificate\_status](#output\_acm\_certificate\_status) | Status of the certificate. |
| <a name="output_arn"></a> [arn](#output\_arn) | The ARN of the Certificate. |
| <a name="output_id"></a> [id](#output\_id) | The ID of the Certificate. |
| <a name="output_tags"></a> [tags](#output\_tags) | A mapping of tags to assign to the resource. |
| <a name="output_validation_route53_record_fqdns"></a> [validation\_route53\_record\_fqdns](#output\_validation\_route53\_record\_fqdns) | List of FQDNs built using the zone domain and name. |

### 💙 Maintained by Rahul Yadav

CEO & CTO at [PrimeOps Technologies](https://primeops.co.in/)  
Helping teams build stable, scalable and consistent cloud and DevOps infrastructure.

<!-- END_TF_DOCS -->


