- Main original purposes
    - effective collaboration
    - empower developers
        - BUT without giving credentials previous to approve

- Terraform workflows
    - just using master
      - `terraform …` locally
      - Problems
          - NO collaboration
          - NO code review
    - PR
      - using PR branch
        - `terraform plan` locally
          - once PR approved → `terraform apply`
      - Problems
        - difficult to estimate the diff
          - **Reason:** 🧠There is NO `terraform plan` ’s output 🧠
        - master is outsync what’s been applied
          - **Reason:** 🧠`terraform apply` could fail & master NOT been aware of that 🧠
    - Atlantis workflow
      - problems of previous approaches are fixed