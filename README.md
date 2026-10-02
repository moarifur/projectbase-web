# Initialize and Push a Local Project to GitHub

This guide documents the Git setup and first push of the `projectbase-web` project to GitHub.

## 1. Navigate to the Project

Open PowerShell and move into the project directory:

```powershell
cd C:\Users\moarifur\Music\projectbase\projectbase-web
```

## 2. Initialize Git

Create a new Git repository:

```powershell
git init
```

Expected output:

```text
Initialized empty Git repository in .../projectbase-web/.git/
```

## 3. Verify Git Credential Manager

Check the installed Git Credential Manager version:

```powershell
git credential-manager --version
```

Example result:

```text
2.9.0+194ba290ce533465310d50f811684ab180536ae7
```

## 4. Clear Existing GitHub Credentials

Remove the existing GitHub HTTPS credentials from Git Credential Manager:

```powershell
git credential-manager erase
```

Then provide:

```text
protocol=https
host=github.com
```

This ensures GitHub authentication starts cleanly when pushing.

## 5. Create the Initial Commit

An initial commit cannot be created until files are staged.

The first attempt:

```powershell
git commit -m "Where content meets automation"
```

reported that the project files were untracked.

Stage the project:

```powershell
git add .
```

Git may display warnings such as:

```text
LF will be replaced by CRLF
```

These are line-ending warnings and did not prevent the files from being staged.

Now create the initial commit:

```powershell
git commit -m "Where content meets automation"
```

The project was successfully committed:

```text
[master (root-commit) 4d83cf1] Where content meets automation
48 files changed, 31890 insertions(+)
```

> **Important:** The `.env` file was included in this commit. Before pushing projects to a public repository, verify that `.env` does not contain passwords, API keys, tokens, database credentials, or other secrets.

## 6. Add the GitHub Remote

Connect the local repository to GitHub:

```powershell
git remote add origin https://github.com/moarifur/projectbase-web.git
```

## 7. Rename the Default Branch

Rename the local `master` branch to `main`:

```powershell
git branch -M main
```

## 8. Push the Project to GitHub

Push the `main` branch and establish its upstream tracking relationship:

```powershell
git push -u origin main
```

GitHub requested browser authentication:

```text
info: please complete authentication in your browser...
```

After authentication, Git successfully uploaded the repository:

```text
To https://github.com/moarifur/projectbase-web.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

## 9. Result

The local `projectbase-web` repository is now connected to:

```text
https://github.com/moarifur/projectbase-web.git
```

The `main` branch is configured to track `origin/main`.

For future changes, the basic workflow is:

```powershell
git add .
git commit -m "Describe the change"
git push
```
