---
date: 2020-03-19

linktitle: Deploying a static website using GitHub Actions
title: Deploying a static website using GitHub Actions
icon: cloud-upload
summary: How to deploy a Hugo generated website using GitHub Actions.
draft: false
---

I built this website using [Hugo](https://gohugo.io/), it's one of the most popular open-source static site generators.

I wanted to deploy on `push` to my [Droplet in DigitalOcean](https://www.digitalocean.com/products/droplets/) and I started using [GitHub Actions](https://github.com/features/actions) for that. It's a very good tool to automate CI/CD and is straightforward to set-up.

Here are the steps I followed to automate my deployment - since it's just a personal website and I'm the only one who makes changes, I deploy on `push` to `master`. You will need to:

1. [Create a SSH key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
2. Add the following [Secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) to GitHub:
    - `HOST`: your website hostname.
    - `USERNAME`: the username you'd like to use to SSH into your remote server.
    - `KEY`: SSH key created in step 1.
    - `PORT`: this should be `22`.
3. Create a new directory in your repo `.git/workflow` and add a new YAML file. 

    In the script section, we are pulling the changes from GitHub, generating the static files using `hugo` command, and copying the content of the public folder into the directory served by the web server used.

        name: deploy

        on: [push]

        jobs:
          build:

            runs-on: ubuntu-latest
        
            steps:
            - name: executing remote ssh commands using key
              uses: appleboy/ssh-action@master
              with:
                host: ${{ secrets.HOST }}
                username: ${{ secrets.USERNAME }}
                key: ${{ secrets.KEY }}
                port: ${{ secrets.PORT }}
                script: cd /path/to/repo; git pull; hugo; cp -r ./public/* /path/to/serve/directory/.; rm -rf ./public

4. Commit & push to GitHub, this will kick-off the workflow created in step 3.

![Hola](/workflow.png)

If your workflow fails, you can check the logs by clicking on `Details`.

Let me know if you need help with any of the steps above ✨ you can reach out to me on [Twitter](https://twitter.com/salwa_fathallah)!
