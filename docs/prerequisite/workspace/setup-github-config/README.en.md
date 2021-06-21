---
title: Setup github account in cloud9 workspace
weight: 6
---

1, Set up git with your user name and email through following commands, please replace `Your name here` and `your_email@example.com` with your github account.

```sh
git config --global user.name "Your name here"
git config --global user.email "your_email@example.com"
```

2, Set up ssh on your cloud9 workspace.

Check if you have files ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub. if not, please follow [Create an SSH key](https://gcr-solutions.github.io/recommender-system-dev-workshop-code/prerequisite/workspace/create-ssh-key/readme/) to create such public/private keys.

Copy your public key (content of ~/.ssh/id_rsa.pub file) into your clipboard.

3, Paste your ssh public key into your github account settings.
- Go to your github [Account Settings](https://github.com/settings/profile)
- Click [SSH and GPG keys](https://github.com/settings/keys) in the left sidebar.
- Click **New SSH key** on the top right.
![Github SSH New](/images/github-ssh-new.png)

- Add a label (like “My Cloud9”) and paste the public key into the big text box.
![Paste Github SSH key](/images/paste-github-ssh-key.png)

4, Test your configuration through the following command:
```sh
ssh -T git@github.com
```
Type `yes` and press `enter`.

If it says something like the following, it worked:
`Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.`


