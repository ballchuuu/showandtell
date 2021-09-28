# Show and tell: Telegram Notification for Every Push and Pull Request

#### Aim:
To utilise GitHub actions to provide a workflow that triggers a notification when there is a push or pull request.

#### Process of setting up the workflow:
1. Creating the API token via @BotFather on Telegram
2. Obtaining my own chat ID via the getUpdate Telegram
3. Place the above token and chat ID as secrets in GitHub
4. Adding the yaml file as seen below to GitHub Actions

```
name: telegram-notify

on: [push, pull_request]
  
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Update status
      uses: ballchuuu/showandtell@master
      with:
        to: ${{ secrets.TELEGRAM_TO }}
        token: ${{ secrets.TELEGRAM_TOKEN }}
        message: |
          ${{ github.event_name }} commit in ${{ github.repository }} by "${{ github.actor }}". [${{github.sha}}@${{ github.ref }}]
```
