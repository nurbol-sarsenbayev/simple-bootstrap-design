# Простой Bootstrap шаблон

Привет, здесь мы расмотрим простую адаптивную верстку на больших, средних и маленьких экранах для обучения новичков. Шаблон скачиваете по этой [ссылке](https://github.com/nurbol-sarsenbayev/nurbol-sarsenbayev.github.io/raw/master/psd_templates/simple_bootstrap_template.psd). А готовую верстку можно посмотреть [здесь](https://nurbol-sarsenbayev.github.io/tutorials/simple-bootstrap-design/).



## Подготовка среды
1. [**NodeJS**](https://nodejs.org/en/) — среда, на котором запускается ниже перечисленные инструменты. Необходимо установить, если не установлен на вашем компьютере;
2. **Gulp** — для автоматизации рутинных задач. Устанавливается глобально командой `npm install -g gulp` в терминале;
3. [**Стартовый шаблон**](https://github.com/nurbol-sarsenbayev/start-template-gulp) — скачиваем и установливаем все node модули указанные в package.json проекта запустив команду `npm install` в командной строке (cmd) открыв его в корневой папке проекта (после скачивания имя корневой папки будет start-template-gulp). Потом поменяем название короневой папки и проекта в package.json и bower.json с start-template-gulp на simple-bootstrap-design или на то, как хотите назвать проекта. Не забываем менять и описание проекта в package.json и bower.json.
Если не понятно структура стартового шаблона, рекомендую прочитать его инструкцию [здесь](https://github.com/nurbol-sarsenbayev/simple-bootstrap-design/blob/master/README.md).
4. Удаляем шрифты с файла **app/sass/\_fonts.scss** и с папки **app/fonts** кроме шрифта _Fontawesome_, так как в нашем шаблоне используется шрифт _Arial_, который поддерживается на всех браузерах. В шаблоне еще используется шрифт _Socialico_ для отображения иконок. Но мы вместо этого шрифта будем использовать _Fontawesome_. 
