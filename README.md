# Code-Shamer Custom Action

**Enforces Python code quality and shames perpetrators on Telegram for crimes against Clean Code.**

This Composite GitHub Action runs strict static analysis on your Python code using `flake8`. If it detects style violations, unused variables, or a cyclomatic complexity higher than 10, the build fails and the author of the commit is publicly shamed in a Telegram chat.

## 📦 Prerequisites

You need a Telegram Bot and a Chat ID. Add them to your repository secrets:
* `TELEGRAM_TOKEN`: Your bot's API token.
* `TELEGRAM_CHAT_ID`: The ID of the chat/group where the bot will send the shame message.

## 🚀 Usage

Add this step to your `.github/workflows/main.yml` file. 
*(Make sure to run `actions/checkout` first so the action has access to your code).*
```yaml
jobs:
  lint-and-shame:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Run Code-Shamer
        uses: cs-2526-grupo-1/code-shamer@v2.1
        with:
          telegram_token: ${{ secrets.TELEGRAM_TOKEN }}
          telegram_chat_id: ${{ secrets.TELEGRAM_CHAT_ID }}
