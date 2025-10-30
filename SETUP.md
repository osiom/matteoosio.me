# INIT.md

> 🚀 **MacBook M1 Developer Setup Guide**
>
> This guide sets up a modern, productive development environment on a new MacBook (Apple Silicon).
>
> Includes:
> - iTerm2 (modern terminal)
> - Zsh + Oh My Zsh
> - Spaceship Prompt (with Git branch visibility)
> - `uv` (Python versions, envs, and packages)
> - Git, Docker, Node.js
> - Useful CLI tools (`tree`, `bat`)

---

## 🧩 1. Install Homebrew (Apple Silicon)

Homebrew is the package manager used to install most tools.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After install, add Homebrew to your PATH:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Verify:

```bash
brew --version
```

---

## 💻 2. Install iTerm2

```bash
brew install --cask iterm2
```

Then open iTerm2 and make it your default terminal (`iTerm2 > Make iTerm2 Default Term`).

---

## ⚙️ 3. Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## 🌌 4. Install Spaceship Prompt (with Git branch visibility)

```bash
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Edit your `~/.zshrc`:

```bash
ZSH_THEME="spaceship"
```

Reload zsh:

```bash
source ~/.zshrc
```

### 🪄 Optional — Customize Spaceship Prompt

Add this block in your `~/.zshrc` below the theme line:

```bash
SPACESHIP_PROMPT_ORDER=(
  user
  dir
  git
  node
  python
  exec_time
  line_sep
  time
  char
)

SPACESHIP_GIT_BRANCH_SHOW=true
SPACESHIP_GIT_STATUS_SHOW=true
SPACESHIP_PROMPT_ADD_NEWLINE=true
```

Then reload again with `source ~/.zshrc`.

---

## 🐍 5. Install `uv` (Python versions, environments & packages)

[`uv`](https://docs.astral.sh/uv/) is a fast and modern Python manager that replaces `pyenv`, `venv`, and `pip`.

```bash
brew install uv
```

Verify:

```bash
uv --version
```

### 🧠 Common `uv` Commands

| Task | Command |
|------|----------|
| Install latest Python | `uv python install` |
| Install specific version | `uv python install 3.12` |
| List installed versions | `uv python list` |
| Create new env | `uv init` |
| Add packages | `uv add requests flask` |
| Update packages | `uv update` |
| Sync project deps | `uv sync` |

---

## 🧰 6. Install Essential Developer Tools

### 🔧 Git

```bash
brew install git
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Verify:

```bash
git --version
```

---

### 🐋 Docker

```bash
brew install --cask docker
```

Open **Docker.app** once and let it complete setup.

---

### 🧠 Node.js (with npm)

```bash
brew install node
```

Verify:

```bash
node -v
npm -v
```

---

### 🗂️ CLI Utilities (recommended)

```bash
brew install tree bat
```

- `tree` — visual directory structure
- `bat` — modern `cat` with syntax highlighting

---

## ✅ Final Check

Restart iTerm2 and confirm everything:

```bash
echo $SHELL
zsh --version
git --version
docker --version
node -v
uv --version
spaceship
```

You now have:
- 🧠 Zsh with Spaceship Prompt
- 🐍 `uv` for Python
- 🐋 Docker for containers
- 🧩 Git + Node.js for version control & JS tools
- ⚙️ Handy CLI tools for daily work

---

**Next steps:**
- Install VS Code: `brew install --cask visual-studio-code`
- Set up SSH keys: `ssh-keygen -t ed25519 -C "you@example.com"`
- Connect GitHub via `gh auth login`

🎉 You’re ready to code productively on your new MacBook M1!
