# GITHUB_SSH_SETUP
 GitHub's SSH and GPG keys settings is simply a way to label your SSH key for easy identification.

1.  **Check for Existing SSH Keys**

Before creating a new SSH key, check if you already have one:

```sh
ls -al ~/.ssh
```

If you see files like id_rsa.pub or id_ed25519.pub, you already have an SSH key.



**2. Generate a New SSH Key**

```sh
ssh-keygen -t ed25519 -C "your-email@example.com"
```

f ed25519 is not supported, use RSA:

```sh
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```
When prompted, press Enter to save it in the default location (~/.ssh/id_ed25519 or ~/.ssh/id_rsa).


**3.  Add SSH Key to the SSH Agent**

start SSH

```sh
eval "$(ssh-agent -s)"
```
Add SSH 

```sh
ssh-add ~/.ssh/id_ed25519 or ssh-add ~/.ssh/id_rsa
```

**4. Copy the SSH Public Key**

```sh
cat ~/.ssh/id_ed25519.pub or cat ~/.ssh/id_rsa.pub
```
**5. Add SSH ket to the GitHub or GitLab**

**6. Test SSH Connection**
```sh
ssh -T git@github.com
```
**6. Ensure the SSH Agent is Running**

Start the SSH agent:
```sh
eval "$(ssh-agent -s)"
```
Then add your private key:
```sh
ssh-add ~/.ssh/id_ed25519
```

If you're using an RSA key, replace with:
```sh
ssh-add ~/.ssh/id_rsa
```
**8. Set Correct SSH Key Permissions**

```sh
chmod 600 ~/.ssh/id_ed25519
chmod 600 ~/.ssh/id_ed25519.pub
```
