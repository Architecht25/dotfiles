# Dotfiles

Configuration personnelle du shell, de Git, de Ruby, de SSH et de VS Code, installée
par des liens symboliques. Ce dépôt est un fork de
[lewagon/dotfiles](https://github.com/lewagon/dotfiles) : il reprend l'outillage
des bootcamps Le Wagon (oh-my-zsh, plugins, pry) et y ajoute ses propres réglages
(`gitconfig` est modifié localement et n'est pas encore commité).

## Fichiers

| Fichier | Installé comme | Rôle |
|---------|----------------|------|
| `zshrc` | `~/.zshrc` | oh-my-zsh (thème `robbyrussell`), plugins, chargement de rbenv, pyenv, nvm, `nvm use` automatique via `.nvmrc` |
| `zprofile` | `~/.zprofile` | PATH pour pyenv et Homebrew |
| `aliases` | `~/.aliases` | alias (`myip`, `serve`, `stt`…) |
| `gitconfig` | `~/.gitconfig` | configuration Git |
| `irbrc` | `~/.irbrc` | configuration IRB |
| `pryrc` | `~/.pryrc` | prompt Pry qui affiche le nom de l'application Rails et son environnement |
| `rspec` | `~/.rspec` | options RSpec (`--color --format documentation`) |
| `config` | `~/.ssh/config` (macOS uniquement) | options SSH, clé `id_ed25519` chargée dans le trousseau |
| `settings.json` | VS Code `settings.json` | réglages de l'éditeur |
| `keybindings.json` | VS Code `keybindings.json` | raccourcis (coller avec indentation) |

## Installation

```bash
./install.sh
```

Le script :

1. déplace les fichiers existants (non symboliques) en `*.backup` et crée les liens
   vers ce dépôt, pour `aliases`, `gitconfig`, `irbrc`, `pryrc`, `rspec`, `zprofile`
   et `zshrc` ;
2. installe les plugins oh-my-zsh `zsh-autosuggestions` et `zsh-syntax-highlighting` ;
3. relie les réglages VS Code (macOS, Linux ou WSL) ;
4. sur macOS, relie `~/.ssh/config` et ajoute la clé SSH au trousseau ;
5. relance `zsh`.

Les liens ne sont créés que si la cible n'existe pas déjà.

## Identité Git

```bash
./git_setup.sh
```

Ce script demande un nom et un email, les écrit dans la configuration Git globale, puis
crée un commit, le pousse sur `origin master` et ajoute le remote `upstream` pointant
vers `lewagon/dotfiles`. Il est écrit pour le bootcamp : **ne pas le lancer tel quel**
sur ce fork, il pousserait un commit sur `master`.

## Dépendances attendues

- oh-my-zsh
- Visual Studio Code (pour les réglages éditeur)
- Git
- rbenv, pyenv et nvm, optionnels : le shell les charge seulement s'ils sont installés
