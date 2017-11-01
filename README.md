# Простой Bootstrap шаблон

Привет, здесь мы расмотрим простую адаптивную верстку на больших, средних и маленьких экранах для обучения новичков. Макет скачиваете по этой [ссылке](https://github.com/nurbol-sarsenbayev/nurbol-sarsenbayev.github.io/raw/master/psd_templates/simple_bootstrap_template.psd). А готовую верстку можно посмотреть [здесь](https://nurbol-sarsenbayev.github.io/tutorials/simple-bootstrap-design/).


## Подготовка среды
1. [**NodeJS**](https://nodejs.org/en/) — среда, на котором запускается ниже перечисленные инструменты. Необходимо установить, если не установлен на вашем компьютере.
2. **Gulp** — для автоматизации рутинных задач. Устанавливается глобально командой `npm install -g gulp` в терминале.
3. [**Стартовый шаблон**](https://github.com/nurbol-sarsenbayev/start-template-gulp) — скачиваем и установливаем все node модули указанные в package.json проекта запустив команду `npm install` в командной строке (cmd) открыв его в корневой папке проекта (после скачивания имя корневой папки будет start-template-gulp). Не закрывайте эту командную строку, так как вы будете пользоваться им для разработки. Потом поменяем название короневой папки и проекта в package.json и bower.json с start-template-gulp на simple-bootstrap-design или на то, как хотите назвать проекта. Не забываем менять и описание проекта в package.json и bower.json.
Если не понятно структура стартового шаблона, рекомендую прочитать его инструкцию [здесь](https://github.com/nurbol-sarsenbayev/simple-bootstrap-design/blob/master/README.md).
4. Удаляем шрифты с файла **app/sass/\_fonts.scss** и с папки **app/fonts** кроме шрифта _Fontawesome_, так как в нашем шаблоне используется шрифт _Arial_, который поддерживается на всех браузерах. В шаблоне еще используется шрифт _Socialico_ для отображения иконок. Но мы вместо этого шрифта будем использовать _Fontawesome_. 
5. Выполняем команду `gulp` в терминале (открытый в пункте 9) для запуска проекта.


## Photoshop
Для этого урока у вас должен быть установлен Фотошоп, чтобы открыть макет и уметь пользоваться Фотошопом. Если не хватает умения, я рекомендую посмотреть эти видеоуроки [Урок 1](https://www.youtube.com/watch?v=rXjq9rnbltk&list=PLbZerpEHZ8s3cd2imWUFvG4AFBKMaBg4S) и [Урок 2](https://www.youtube.com/watch?v=nBY7JdMuvMA&index=2&list=PLbZerpEHZ8s3cd2imWUFvG4AFBKMaBg4S) прежде чем продолжить урок. 

## Bootstrap
Для сетки сайта используем адаптивную Bootstrap сетку 3 версии. Если не знакомы, рекомендуем прочитать систему сеток Bootstrap [здесь](http://bootstrap-3.ru/css.php#grid). Если кратко, сетка Bootstrap будет таким:
```
<div class="container">
  <div class="row">
    <div class="col-sm-7"></div>
    <div class="col-sm-5"></div>    
  </div>
</div>
```
Сетка должен начинаться с блока классом **container** (есть еще container-fluid, но мы его не рассмотриваем) в котором будет блоки с классами **row** обозначающий строку сетки. В каждой строке будет столбцы с классами **col-sm-\***, где будет указано сколько колонок будет занимать каждый столбец. Сумма колонок столбцов в одной строке должен быть 12.  


## Разработка

Анализируя макет, создаем такую html стурктуру в **app/index.html**. 
```
<div id="page-wrapper">
  <header class="page-header"></header>
  <section class="s-plusess"></section>
  <section class="s-about"></section>
  <section class="s-screenshots"></section>
  <section class="s-reviews"></section>
  <section class="s-prices"></section>
  <section class="s-contacts"></section>
  <footer class="page-footer"></footer>
</div>
```
Есть один блок page-wrapper в котором будет все секции макета и header, footer. Чтобы выделить классы секций с остальных классов, вставим **s-** перед классами секций. 

### Header

```
<header class="page-header">
  <div class="container">
    <div class="row">
      <div class="col-sm-7">
        <h1 class="h1">Product name</h1>
        <ul class="header-list">
          <li>Put on this page information about your product</li>
          <li>A detailed description of your product</li>
          <li>Tell us about the advantages and merits</li>
          <li>Associate the page with the payment system</li>
        </ul>
      </div>
      <div class="col-sm-5">
        <div class="header-img back-white"></div>
      </div>
    </div>
  </div>
</header>
```



