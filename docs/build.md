## Сборка и деплой KomBot

Ниже даны пошаговые инструкции по локальной сборке, проверке и подготовке артефактов для деплоя.

### Требования
- Node.js (рекомендуется LTS)
- npm

### Подготовка
1. Переименуйте `package-sample.json` в `package.json`:

```bash
mv package-sample.json package.json
```

2. Установите зависимости:

```bash
npm install
```

### Быстрая сборка

```bash
npm run build
```

Это выполнит `build:css`, `build:js`, `build:images` и положит сгенерированные файлы в `dist/`.

### Режим разработки (live-reload)

```bash
npm run watch
```

Это запустит `browser-sync` и наблюдение за изменениями в `src/`.

### Обновление инструментов
- `node-sass` помечен как deprecated в пользу `sass` (Dart Sass). Рекомендуется заменить:

1. Установить `sass` и заменить команду `node-sass` на `sass` в `package.json`.
2. Заменить `uglify-es` на `terser` для минификации JS.
3. Обновить `postcss-cli`, `autoprefixer`, `browser-sync` и другие зависимости до актуальных версий.

Пример изменения скрипта `scss`:

```json
"scss": "sass --style=compressed src/scss:dist/css"
```

И минификация JS (пример):

```json
"uglify": "mkdirp dist/js -p && terser src/js/*.js -c -m -o dist/js/main.min.js"
```

### Деплой
- Для статического хоста скопируйте `index.html` и папку `dist/` на сервер.
- GitHub Pages: можно настроить ветку `gh-pages` и публиковать содержимое `dist/`.
- Netlify/Vercel: подключите репозиторий и укажите команду сборки `npm run build` и директорию для деплоя `.` (или `dist/` в зависимости от настройки).

### CI/CD рекомендации
- Не запускайте `postinstall`, если он стартует длительный watch — это может блокировать CI. В CI используйте `npm ci` и `npm run build`.
- Добавьте линтеры и базовые unit-тесты в pipeline.

### Замечания безопасности
- Не храните секреты и ключи в репозитории. Проект — статический, но при добавлении интеграций используйте секреты CI/CD.
