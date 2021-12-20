<!-- start title -->
<!-- end title -->
<!-- start description -->
<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->
# How do I use this repo?

1. Customize `action.yaml`
2. Cusomize the `Example Usage` in the readme (this is the only part of the readme that isn't auto-generated yet)
3. PR into main
4. On PR merge CI will release your action and generate the README.md from the `action.yaml`
<!-- end usage -->
<!-- start inputs -->
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
