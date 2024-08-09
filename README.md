1- Add a secret for actions on your github repository with your Telnyx API Key at TELNYX_API_KEY

2- Create the following file on your repository `.github/workflows/review_pr.yml`

```
name: PR Review

on:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  pull-requests: write

jobs:
  review:
    runs-on: ubuntu-latest

    steps:
      - name: PR Review
        uses: team-telnyx/reviewpr@main
        with:
          telnyx_api_key: ${{ secrets.TELNYX_API_KEY }}
          model_name: 'meta-llama/Meta-Llama-3.1-8B-Instruct'
```
The model name is optional.

Done , The next time a PR is open it will be automatically reviewed by Telnyx Inference.
