# Getting Started

To get started visit [Telnyx Inference documentation](https://developers.telnyx.com/docs/inference/getting-started)

# How to add it to my project?

1. [Add a secret for actions on your github repository](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) with your Telnyx Token at TELNYXAI_TOKEN
1. Create the following file on your repository `.github/workflows/review_pr.yml`

```yaml
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

And done , The next time a PR is open it will be automatically reviewed by Telnyx Inference.
