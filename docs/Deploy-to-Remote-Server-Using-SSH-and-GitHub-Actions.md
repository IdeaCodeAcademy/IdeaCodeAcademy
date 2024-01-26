# Deploy to Remote Server Using SSH and GitHub Actions

## generate private key

```zsh 
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

```zsh
cat ~/.ssh/id_rsa
```

## create github secrets

`settings > Secrets & Variables > Actions > New repository secret`

1. `HOST` - ip
2. `PRIVATE_KEY` - your secret key
3. `USERNAME` - ssh login as user


## add then create in your repo - 



```yml title=".github/workflows/deploy.yml"  linenums="1" hl_lines="5 18 24"
name: Deployment Workflow
on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Set up SSH key
        run: |
          mkdir -p ~/.ssh
          echo "${{ secrets.PRIVATE_KEY }}" > ~/.ssh/id_rsa
          chmod 600 ~/.ssh/id_rsa
          ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts
      - name: Deploy to server
        run: |
          echo "Starting deployment..."
          ssh -i ~/.ssh/id_rsa -o StrictHostKeyChecking=no ${{ secrets.USERNAME }}@${{ secrets.HOST }} "cd /home/github-cicd-to-ssh && git pull origin main && ls"
          echo "Deployment completed."
```

check your github actions and SSH

## if you are using `private` repo -

```zsh
git config --global credential.helper store
```