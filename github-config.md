# GitHub: Personal Access Token (classic) & Git Bash on Windows

## 1. Generate a Personal Access Token (classic) on GitHub

1. Log in to [GitHub](https://github.com).
2. Click your **profile picture** (top right) → **Settings**.
3. In the left sidebar, scroll down and click **Developer settings**.
4. Click **Personal access tokens** → **Tokens (classic)**.
5. Click **Generate new token** → **Generate new token (classic)**.
6. Give the token a **Note** (e.g. "my-token") and choose an **Expiration** (e.g. 90 days or "No expiration" for class use).
7. Under **Scopes**, check at least **repo** (full control of private repositories). Add others only if you need them.
8. Click **Generate token**.
9. **Copy the token immediately** and store it somewhere safe. GitHub will not show it again. If you lose it, you must generate a new token.

---

## 2. Use the token in Git Bash on Windows

When you `git push`, `git pull`, or `git clone` over HTTPS, Git will ask for your credentials.

- **Username:** your GitHub username  
- **Password:** paste your **Personal Access Token** (not your GitHub account password)

Git Bash will prompt in the terminal. Enter the token when it asks for a password.

**Optional – cache the token so you don’t type it every time:**

```bash
git config --global credential.helper store
```

The next time you enter your username and token, Git will save them (in plain text) and reuse them for future HTTPS operations. Only do this on a machine you control.

**To stop caching credentials later:**

```bash
git config --global --unset credential.helper
```
