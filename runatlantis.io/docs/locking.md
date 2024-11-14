# Locking

* 👀if `plan` is run -> directory & Terraform workspace are **Locked** 👀 
  * != WHOLE repo locked
  * UNTIL 
    * PR is
      * merged or
      * closed, or
    * plan is manually deleted
  * if ANOTHER user attempts to `plan` | 👀SAME directory and workspace👀 | different PR -> they'll see this error 

    ![Lock Comment](./images/lock-comment.png)

    linked to the PR / holds the lock

## Why

* locking
  * -- ensures that -- NO other changes will be made UNTIL the PR is merged
    * 👀`atlantis apply` & BEFORE the PR is merged -> your `main` branch is NOT the MOST up to date version of your infrastructure 👀
  * why NOT apply | merge?
    * if `terraform apply` fails & PR ALREADY merged -> you would need to create a NEW PR

## Viewing Locks

* URL | Atlantis is hosted at

    ![Locks View](./images/locks-ui.png)

    * click | locked -- to view -- its details

        <p align="center">
            <img src="./images/lock-detail-ui.png" alt="Lock Detail View" height="400px">
        </p>

## Unlocking

* 👀ways to unlock 👀
  * PR is merged or closed
  * comment `atlantis unlock` | PR
  * click **"To discard this plan click here"** | bottom of the plan comment & reject | UI

    ![Locks View](./images/lock-delete-comment.png)

    -- redirect to -- 

    <p align="center">
        <img src="./images/lock-detail-ui.png" alt="Lock Detail View" height="400px">
    </p>

* ONCE a plan is discarded & you want to raise up that PR -> you'll need to run `plan` again

## Relationship to Terraform State Locking

* 💡Atlantis does NOT conflict with [Terraform State Locking](https://developer.hashicorp.com/terraform/language/state/locking) 💡
  * Reason: 
    * Atlantis 
      * run `terraform plan` and `apply` / locking by Terraform is NOT affected
      * prevents MULTIPLE PR | SAME state
    * Terraform state locking locks the state | run `terraform apply` -> MULTIPLE applies can NOT run concurrently
