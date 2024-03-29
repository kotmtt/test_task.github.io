#  Frontend boilerplate template
Сборщик Twig, SCSS (SASS), js (es6), json

## Подготовка
Для начала разработки необходимо клонировать репозиторий к себе
```
// клонирование в папку <project>
git clone <ссылка на репозиторий> <project>
```
~
## Запуск
```bash
npm i            # установка зависимостей
npm run "<task>" # запуск сценария
                 # <start>, <build>, <build:assets>
```

## Работа со сборщиком
### Компоненты
Находятся в папке `src/include/@atoms/` (`src/include/^molecules/`, `src/include/&organisms`), могут содержать в себе файлы с расширениями `scss (sass) / twig / js / json`. Названия файлов должны быть либо `index`, либо должны совпадать с названием компонента (папки).

Пример компонента `button`:
```
button/
├── button.js   // скрипты
├── button.json // данные компонента
├── button.scss // стили
└── button.twig // разметка
```

Использование компонента ```button```:
```twig
{% view '@button' %}
или с данными
{% view '@button' with {button: {param1: 1, param2: 2}} %}
{% view '@button' with {button: button_in_footer} %}

{% view '@button' with button_in_footer %} // Это будет работать только если внутри button_in_footer есть объект 'button'. Например:
{
    ...
    "button": {
        "text": "example"
    }
    ...
}

```

```@``` - это алиас для компонентов в папке ```@atoms```,
```^``` - это алиас для компонентов в папке ```^molecules```,
```&``` - это алиас для компонентов в папке ```&organisms```.

## Запуск сборщика
Запуск локального сервера
```
npm run start

"start": "cross-env NODE_ENV=development TPL=express webpack-dev-server --colors --progress --hot --inline",
```
Запуск промежуточной сборки
```
npm run build

"build": "cross-env NODE_ENV=development webpack --colors --progress"
```
Запуск сборки для прода
```
npm run build:assets

"build:assets": "cross-env NODE_ENV=production TPL=none webpack --colors --progress"
```

## Решение проблем
### В случае не хватки памяти (обвала сборщика)
Прописываем в package.json
```
"scripts": {
    "dev": "node --max-old-space-size=8192 node_modules/cross-env/src/bin/cross-env NODE_ENV=development node_modules/webpack-dev-server/bin/webpack-dev-server.js"
}
```‣整瑳琭獡੫