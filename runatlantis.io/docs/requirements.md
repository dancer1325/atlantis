# Requirements

* Atlantis
  * ALLOWED | MOST
    * Git hosts
    * Terraform setups

## Git Host

* == Git hosts | Atlantis -- can integrate -- with
  * GitHub (public, private or enterprise)
  * GitLab (public, private or enterprise)
  * Gitea (public, private and compatible forks like Forgejo)
  * Bitbucket Cloud aka bitbucket.org (public or private)
  * Bitbucket Server aka Stash
  * Azure DevOps

## Terraform State

* TODO:
Atlantis supports all backend types **except for local state**. We don't support local state
because Atlantis does not have permanent storage and it doesn't commit the new
statefile back to version control.

:::tip
If you're looking for an easy remote state solution, check out [free remote state](https://app.terraform.io)
storage from Terraform Cloud. This is fully supported by Atlantis.
:::

## Repository Structure

Atlantis supports any Terraform repository structure, for example:

### Single Terraform Project At Repo Root

```plain
.
├── main.tf
└── ...
```

### Multiple Project Folders

```plain
.
├── project1
│   ├── main.tf
|   └── ...
└── project2
    ├── main.tf
    └── ...
```

### Modules

```plain
.
├── project1
│   ├── main.tf
|   └── ...
└── modules
    └── module1
        ├── main.tf
        └── ...
```

With modules, if you want `project1` automatically planned when `module1` is modified
you need to create an `atlantis.yaml` file. See [atlantis.yaml Use Cases](repo-level-atlantis-yaml.md#configuring-planning) for more details.

### Terraform Workspaces

*See [Terraform's docs](https://developer.hashicorp.com/terraform/language/state/workspaces) if you are unfamiliar with workspaces.*

If you're using Terraform `>= 0.9.0`, Atlantis supports workspaces through an
`atlantis.yaml` file that tells Atlantis the names of your workspaces
(see [atlantis.yaml Use Cases](repo-level-atlantis-yaml.md#supporting-terraform-workspaces) for more details)

### .tfvars Files

```plain
.
├── production.tfvars
│── staging.tfvars
└── main.tf
```

For Atlantis to be able to plan automatically with `.tfvars files`, you need to create
an `atlantis.yaml` file to tell it to use `-var-file={YOUR_FILE}`.
See [atlantis.yaml Use Cases](custom-workflows.md#tfvars-files) for more details.

### Multiple Repos

Atlantis supports multiple repos as well–as long as there is a webhook configured
for each repo.

## Terraform Versions

Atlantis supports all Terraform versions (including 0.12) and can be configured
to use different versions for different repositories/projects. See [Terraform Versions](terraform-versions.md).

## Next Steps

* If your Terraform setup meets the Atlantis requirements, continue the installation
  guide and set up your [Git Host Access Credentials](access-credentials.md)
