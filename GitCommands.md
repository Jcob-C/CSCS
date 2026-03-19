# 📘 Git Commands

# 🔧 1. Git Configuration

## Command

```
git config --global user.name "Your Name"
```

### Breakdown

* `git` → the Git program
* `config` → used to configure Git settings
* `--global` → apply this setting to all repositories on your system
* `user.name` → the configuration key (your username)
* `"Your Name"` → the value being assigned

---

## Command

```
git config --global user.email "you@example.com"
```

### Breakdown

* `user.email` → sets your email for commits

---

# 📁 2. Creating & Cloning Repositories

## Command

```
git init
```

### Breakdown

* `init` → initializes a new Git repository in the current folder

---

## Command

```
git clone <repository-url>
```

### Breakdown

* `clone` → copies an existing repository
* `<repository-url>` → the link to the repo (HTTPS or SSH)

---

# 📌 3. Staging & Committing Changes

## Command

```
git status
```

### Breakdown

* `status` → shows current state (modified, staged, untracked files)

---

## Command

```
git add <file>
```

### Breakdown

* `add` → stages changes
* `<file>` → specific file to stage

---

## Command

```
git add .
```

### Breakdown

* `.` → means “all files in current directory”

---

## Command

```
git commit -m "message"
```

### Breakdown

* `commit` → saves changes to history
* `-m` → flag for commit message
* `"message"` → description of changes

---

# 🌿 4. Branching

## Command

```
git branch
```

### Breakdown

* `branch` → lists branches

---

## Command

```
git branch <branch-name>
```

### Breakdown

* creates a new branch

---

## Command

```
git checkout <branch-name>
```

### Breakdown

* `checkout` → switches branches

---

## Command

```
git checkout -b <branch-name>
```

### Breakdown

* `-b` → create + switch in one step

---

# 🔀 5. Merging

## Command

```
git merge <branch-name>
```

### Breakdown

* `merge` → combines another branch into current branch

---

# 🔄 6. Remote Repositories

## Command

```
git remote add origin <url>
```

### Breakdown

* `remote` → manage remote repos
* `add` → add a new remote
* `origin` → default name for main remote
* `<url>` → repo URL

---

## Command

```
git push origin main
```

### Breakdown

* `push` → upload commits
* `origin` → remote name
* `main` → branch being pushed

---

## Command

```
git pull origin main
```

### Breakdown

* `pull` → fetch + merge

---

## Command

```
git fetch
```

### Breakdown

* downloads changes but does NOT merge

---

# 🧹 7. Undoing Changes

## Command

```
git restore <file>
```

### Breakdown

* restores file to last committed state

---

## Command

```
git reset <file>
```

### Breakdown

* unstages a file

---

## Command

```
git reset --hard
```

### Breakdown

* `--hard` → removes all changes permanently

---

# 📜 8. Viewing History

## Command

```
git log
```

### Breakdown

* shows commit history

---

## Command

```
git log --oneline
```

### Breakdown

* `--oneline` → compact view

---

# 🔍 9. Comparing Changes

## Command

```
git diff
```

### Breakdown

* shows unstaged changes

---

## Command

```
git diff --staged
```

### Breakdown

* shows staged changes

---

# 🏷️ 10. Tagging

## Command

```
git tag v1.0
```

### Breakdown

* `tag` → marks a release point
* `v1.0` → tag name

---

# 🧠 Pro Tips

* Git has **three main areas**:

  * Working Directory (your files)
  * Staging Area (prepared changes)
  * Repository (saved history)

* Think of workflow as:

```
edit → add → commit → push
```

---

# 🚀 Summary Table

| Command    | Purpose          |
| ---------- | ---------------- |
| git init   | Start repo       |
| git clone  | Copy repo        |
| git add    | Stage changes    |
| git commit | Save changes     |
| git push   | Upload changes   |
| git pull   | Download changes |
| git branch | Manage branches  |
| git merge  | Combine branches |

---