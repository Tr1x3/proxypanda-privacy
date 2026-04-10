# Деплой privacy на GitHub Pages

Ниже шаги для постоянной ссылки в формате:

- `https://<github-username>.github.io/proxypanda-privacy/privacy/`

## 1) Авторизация GitHub CLI

Команда:

```powershell
& "C:\Program Files\GitHub CLI\gh.exe" auth login --hostname github.com --web --git-protocol https --skip-ssh-key
```

## 2) Создание и публикация

Запусти команды в папке `privacy-site`:

```powershell
git init
git checkout -b main
git add .
git commit -m "Deploy ProxyPanda privacy site"
& "C:\Program Files\GitHub CLI\gh.exe" repo create proxypanda-privacy --public --source . --remote origin --push
& "C:\Program Files\GitHub CLI\gh.exe" api --method POST repos/{owner}/proxypanda-privacy/pages --field source[branch]=main --field source[path]=/
```

## 3) Готовая ссылка

После включения Pages:

- `https://<github-username>.github.io/proxypanda-privacy/privacy/`

Эту ссылку вставь в:

- `.env` -> `PRIVACY_POLICY_URL=...`
- BotFather description
