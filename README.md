# SecureStack GitHub Actions

A GitHub Action to execute SecureStack application attack surface analysis an application.

```
name: Example Workflow Using SecureStack Action
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo for running code analysis within workflow
        id: checkout
        uses: actions/checkout@v2.4.0
        with:
          fetch-depth: 0
      - name: Code Analysis Step
        id: code
        uses: SecureStackCo/actions-code@main
        with:
          securestack_api_key: ${{ secrets.SECURESTACK_API_KEY_SECRET }}
          securestack_app_id: 'a9ad205b-d519-4a95-833d-304b6e82be21'
          severity: critical
          language: node
          flags: '--path . --debug'
```

## Getting your SecureStack API Key

1. Log in to [SecureStack](https://app.securestack.com) and go to the Profile -> GENERATE KEY screen.
2. Generate an API key and copy the value.
3. Paste into the value of a secret called SECURESTACK_API_KEY_SECRET in the GitHub repo settings.

## Getting your SecureStack Application ID

1. Log in to [SecureStack](https://app.securestack.com).
2. Open the application you wish to analyse.
3. Copy the value of the application id on the View Application screen.
4. Paste into the value of the `securestack_app_id` action input for the step using the SecureStack action in your workflow.


Made with 💜 by SecureStack
