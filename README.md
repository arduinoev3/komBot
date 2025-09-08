## KomBot — landing для мотивации учёбы

KomBot — лёгкий статический лендинг, основанный на шаблоне "Blue". Проект содержит готовую структуру SCSS, минимальную JS-логику для интерактивных компонентов и скрипты для сборки в папку `dist/`.
Цель: простой маркетинговый сайт для продвижения Telegram-наставничества и мотивационных сервисов.

## Основные возможности
- Адаптивный лендинг с секциями: Hero, Features, Pricing, FAQ и Footer.
- SCSS-модульная структура (abstracts / base / components / layout).
- JS для аккордеона, табов и эффектов появления (ScrollReveal).
- Gulp-подобные NPM-скрипты в `package-sample.json` для сборки CSS/JS/изображений и локального сервера.

## Технологический стек
- HTML5, CSS (SCSS)
- JavaScript (ES5/ES6 совместимый)
- Node.js / npm для инструментов разработки
- Инструменты сборки (node-sass, postcss/autoprefixer, uglify, browser-sync и т.д.)

## Быстрый старт
1) Переименуйте `package-sample.json` в `package.json`.
2) Установите зависимости:

```bash
npm install
```

3) Запуск режимов разработки и сборки:

- Полный режим с просмотром и отслеживанием изменений:

```bash
npm run watch
```

- Ручная сборка (CSS, JS, изображения):

```bash
npm run build
```

Примечание: в `package-sample.json` определены отдельные скрипты `build:css`, `build:js`, `build:images`, `watch:css`, `watch:js`, `watch:images`.

## Установка и запуск (детально)
1. Убедитесь, что Node.js >= 8.x и npm установлены.
2. Переименуйте `package-sample.json` → `package.json` и выполните `npm install`.
3. Запустите `npm run watch` для локального сервера (browser-sync). По умолчанию сайт будет доступен по URL, который выведет browser-sync.

## Структура проекта

```
./
├─ index.html                # Входная страница
├─ package-sample.json       # Шаблон package.json (переименуйте)
├─ src/
│  ├─ js/main.js             # Простая логика UI (аккордеон, табы, ScrollReveal)
│  ├─ scss/                  # SCSS-источники
│  │  ├─ abstracts/          # переменные, миксины, функции
│  │  ├─ base/               # базовые стили и утилиты
│  │  ├─ components/         # кнопки, аккордеон, табы
│  │  └─ layout/             # layout секций
│  └─ images/                # исходные SVG/PNG
└─ dist/                     # Сгенерированные артефакты (CSS/JS/images)
```

## Переменные окружения
Проект не требует обязательных runtime-переменных окружения (это статический сайт). Для CI/CD и хостинга вы можете использовать стандартные переменные окружения для Node/npm, если нужно изменить поведение скриптов.

## Тесты
В репозитории нет автоматизированных unit-тестов. Доступны линтеры в `package-sample.json`:

- `npm run lint` — ESLint для `src/js` (в конфиге добрая часть правил стандартного стиля).
- `npm run lint-scss` — stylelint для SCSS.

Рекомендуется добавить простую задачу тестирования и CI (GitHub Actions) при расширении проекта.

## Сборка для продакшна
Скрипт `npm run build` выполняет последовательную сборку CSS, JS и изображений и кладёт результат в `dist/`. Для деплоя копируйте содержимое `dist/` и `index.html` на статический хост (GitHub Pages, Netlify, Vercel и др.).

## Важные нюансы и рекомендации
- `package-sample.json` использует устаревшие версии пакетов (node-sass, uglify-es и др.). Перед развёртыванием рекомендуется обновить зависимости и, при необходимости, заменить deprecated-пакеты (например, `node-sass` → `sass`, `uglify-es` → `terser`).
- Проверяйте пути в `index.html` на совпадение с вашей средой (например, `dist/css/style.css` и `dist/js/main.min.js`).
- Локальная разработка полагается на `browser-sync` и на то, что `postinstall` скрипт может запускать watch — будьте осторожны при CI.

## Автор и лицензия
- Автор: исходный шаблон — Pasquale Vitiello; адаптация — arduinoev3 / Igor.

Licensed under the MIT License — см. файл `LICENSE`.
# Blue

A landing page template.

* [Getting started](#getting-started)

## Getting started
* First, ensure that node.js & npm are both installed. If not, choose your OS and installation method from [this page](https://nodejs.org/en/download/package-manager/) and follow the instructions.
* Next, use your command line to enter your project directory.
* This template comes with a ready-to-use package file called `package-sample.json`. You just need to rename it to `package.json`, then run `npm install` to install all of the dependencies into your project.

You're ready to go! Run any task by typing `npm run task` (where "task" is the name of the task in the `"scripts"` object). The most useful task for rapid development is `watch`. It will start a new server, open up a browser and watch for any SCSS or JS changes in the `src` directory; once it compiles those changes, the browser will automatically inject the changed file(s)!
