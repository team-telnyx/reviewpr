1- Add a secret for actions on your github repository with your Telnyx Token at TELNYXAI_TOKEN

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
          telnyxai_token: ${{ secrets.TELNYXAI_TOKEN }}
          model_name: 'meta-llama/Meta-Llama-3.1-8B-Instruct'
```

Done , The next time a PR is open it will be automatically reviewed by Telnyx Inference.
