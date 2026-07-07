# Инструкция AmneziaVPN — статик сайт

Готовый статический сайт (HTML/CSS + картинки) с пошаговой инструкцией.
Ниже — как выложить его на **GitLab Pages** бесплатно.

## Состав проекта

```
.
├── index.html        # сама страница
├── style.css          # стили
├── images/            # все скриншоты
└── .gitlab-ci.yml     # конфиг для автосборки Pages
```

## Шаги для публикации на GitLab Pages

### 1. Создайте репозиторий на GitLab
- Зайдите на [gitlab.com](https://gitlab.com) и войдите (или зарегистрируйтесь).
- Нажмите **New project → Create blank project**.
- Укажите имя, например `vpn-guide`. Visibility можно оставить **Public** (или Private — Pages всё равно будет работать, доступ к самому сайту настраивается отдельно).
- Нажмите **Create project**.

### 2. Загрузите файлы в репозиторий
Проще всего через веб-интерфейс:
- В репозитории нажмите **+ → Upload file** и по очереди загрузите `index.html`, `style.css`, `.gitlab-ci.yml`.
- Для папки `images/` — либо создайте файл `images/.gitkeep` через **+ → New file** (укажите путь `images/step1.jpg` и т.д.), либо загрузите папку целиком через **+ → Upload file**, если интерфейс это позволяет.

Либо через git (быстрее, если у вас установлен git):

```bash
git clone https://gitlab.com/ВАШ_ЛОГИН/vpn-guide.git
cd vpn-guide
# скопируйте сюда index.html, style.css, images/, .gitlab-ci.yml
git add .
git commit -m "Add VPN guide static site"
git push origin main
```

### 3. Дождитесь сборки
- Перейдите в раздел **Build → Pipelines** в вашем проекте.
- После push автоматически запустится pipeline (job `pages`), который соберёт папку `public/` и опубликует сайт.
- Дождитесь, пока статус станет зелёным (обычно занимает меньше минуты).

### 4. Откройте сайт
- Перейдите в **Deploy → Pages** в левом меню проекта.
- Там будет указан адрес вида:
  ```
  https://ВАШ_ЛОГИН.gitlab.io/vpn-guide
  ```
- Откройте его — сайт готов и общедоступен по этой ссылке.

## Как обновить сайт в будущем
Просто замените/добавьте файлы (например, новые картинки в `images/`) и запушьте изменения — GitLab Pages пересоберёт и обновит сайт автоматически, ничего дополнительно настраивать не нужно.

## Если нужно на GitHub Pages вместо GitLab
Файлы `index.html`, `style.css` и `images/` универсальны и подойдут и для GitHub Pages — `.gitlab-ci.yml` в этом случае не нужен. На GitHub: **Settings → Pages → Source: Deploy from a branch → main / (root)**, и сайт появится по адресу `https://ВАШ_ЛОГИН.github.io/НАЗВАНИЕ_РЕПО`.
