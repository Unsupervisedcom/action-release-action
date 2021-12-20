<!-- start title -->

# GitHub Action:Generate Readme and Release Action

<!-- end title -->
<!-- start description -->

Generates readme from `action.yaml` and Release the action using the given release config

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: Unsupervisedcom/action-release-action@undefined
  with:
    # git token to use for the run
    token: ""

    # If true, this action will disable the `include administrators` setting in branch
    # protection for this branch, and re-enable it after release. Re-enabling is run
    # using always()
    # Default: false
    toggle-admins: ""

    # The release configuration to use for the release. Set this to
    # `@unsupervised/release-config-javascript-actions` for javascript actions
    # Default: @unsupervised/release-config-composite-actions
    release-config: ""
```

<!-- end usage -->
   <!-- start inputs -->

| **Input**            | **Description**                                                                                                                                                                |                   **Default**                    | **Required** |
| :------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------: | :----------: |
| **`token`**          | git token to use for the run                                                                                                                                                   |                                                  |   **true**   |
| **`toggle-admins`**  | If true, this action will disable the `include administrators` setting in branch protection for this branch, and re-enable it after release. Re-enabling is run using always() |                                                  |  **false**   |
| **`release-config`** | The release configuration to use for the release. Set this to `@unsupervised/release-config-javascript-actions` for javascript actions                                         | `@unsupervised/release-config-composite-actions` |  **false**   |

<!-- end inputs -->
   <!-- start outputs -->
   <!-- end outputs -->
   <!-- start examples -->

### Example usage to release on PR merge to main with branch protection enabled

```yaml
name: Semantic Release
on:
  pull_request:
    types:
      - closed
    branches:
      - main
    paths:
      - action.yaml
jobs:
  semantic-release:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    steps:
      - uses: Unsupervisedcom/action-release-action@v1
        with:
          token: ${{ secrets.DEPLOYER_CI_TOKEN }}
          toggle-admins: true
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
