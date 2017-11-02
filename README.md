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
```html
<div class="container">
  <div class="row">
    <div class="col-sm-7"></div>
    <div class="col-sm-5"></div>    
  </div>
</div>
```
Сетка должен начинаться с блока классом **container** (есть еще container-fluid, но мы его не рассмотриваем) в котором будет блоки с классами **row** обозначающий строку сетки. В каждой строке будет столбцы с классами **col-sm-\***, где будет указано сколько колонок будет занимать каждый столбец. Сумма колонок столбцов в одной строке должен быть 12. А также в одной разметке мы можем указать сколько колонок должен занимать столбцы в разных экранах меняя **sm** на **md**, или **lg**, или **xs**. 
* **.col-xs-**: Очень маленькие устройство, Телефоны (<768px)
* **.col-sm-**: Малые устройства, Планшеты (≥768px)
* **.col-md-**: Средние устройства, Настольные (≥992px)
* **.col-lg-**: Большие устройства, Настольные (≥1200px)
Можно скрыть или показать столбцов в конкретных экранах использую **visible-** и **hidden-**:


## Разработка

Анализируя макет, создаем такую html стурктуру в **app/index.html**. 
```html
<div id="page-wrapper">
  <header  class="section section-header section-inverse"></header>
  <section class="section section-about"></section>
  <section class="section section-plusses"></section>
  <section class="section section-screenshots"></section>
  <section class="section section-reviews"></section>
  <section class="section section-prices"></section>
  <section class="section section-contacts section-inverse"></section>
  <footer  class="page-footer"></footer>
</div>
```
Будет один блок **page-wrapper** в котором будет все секции макета и header, footer. Классы секций будет начинаться так **section section-**, чтобы выделить от остальных классов. **section-inverse** означает, что это секция будеть иметь синий фон с белым текстом, когда обычная секция имеет белый фон и черный текст по макету. Все основные css коды пишем в **app/sass/main.scss**. 
```css
.section {
  padding: 50px 0;
  background-color: #fff;
  color: #333;

  &-inverse {
    background-color: #445162;
    color: #fff;
  }
}
```
В фотошопе в макете выбираем основные тексты и смотрям какие у них параметры в окне Character:
![Текст в Фотошопе](https://nurbol-sarsenbayev.github.io/images/simple-bootstrap-design/photoshop_character.JPG)
На рисунке видно, что шрифт (font-family) Arial, размер шрифта (font-size) 16px, высота линии (line-height) 24px, цвет текста (color) черный. Чтобы эти свойствы были заданы на все элементы, а не только к тексту, их пишем в body:
```css
body {
	min-width: 320px;
	position: relative;
	line-height: 24px;
	font-size: 16px;
	font-family: Arial, sans-serif;
	color: #333;
	overflow-x: hidden;
	opacity: 1;
}
```


### Header
Шапка сайта будет выглядет так:
```html
<header class="section section-header section-inverse">
  <div class="container">
    <div class="row">
      
      <div class="col-sm-7">
        <h1 class="h1">Product name</h1>
        <ul class="list list-header">
          <li>Put on this page information about your product</li>
          <li>A detailed description of your product</li>
          <li>Tell us about the advantages and merits</li>
          <li>Associate the page with the payment system</li>
        </ul>
      </div>
      
      <div class="col-sm-5">
        <div class="img-header img img-white"></div>
      </div>
    
    </div>
  </div>
</header>
```
А CSS шапка:
```css
.h1 {
	margin: 0;
	line-height: 1.5;
	font-size: 60px;
	font-weight: normal;
}

.list {
	margin: 0;
	padding: 0;
	list-style: none;
	
	&-header {
		margin-top: 20px;	
		li {
			&:before {
				font-family: "fontawesome";
				content: "\f00c";
				margin-right: 8px;
				font-size: 26px;
			}
			font-size: 20px;
			line-height: 36px;
		}
	}
}
```
В макета высота линии заголовка задан auto, а это значить нам придется задать примерную высоту линию. Лучшии практики будет написать css свойствы на классы, а не на семантические теги. А иконка в макете сделан как рисунок, но в 2017 году иконок в основном делает через шрифт fontawesome. Так как иконка рисунок, мы дадим примерную размер шрифта иконка. Класс списка написан так **class="list list-header"**, чтобы css свйоства осталных секций написать в одном месте.  
```css
.img {
	width: 100%;
	&-white {
		background-color: #fff;
	}

	&-blue {
		background-color: #445161;
	}

	&-header {
		height: 214px;
	}
}
```
Все css-ы рисунков пишем в одном место. В макете нет рисунков, а есть место рисунка. Но мы их будем назвать рисунками для удобства. _img-white_ рисунок с белым фоном, а _img-blue_ с синим фоном. _img-header_ это рисунок секции header. Рисунки остальных секций тоже будет здесь расположены. 

### Секция About
```html
<section class="section section-about">
	<div class="container">
		<div class="row">
			<div class="col-sm-7">
				<h2 class="h2">About your product</h2>
				<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis facilis fuga, 
				illo at. Natus eos, eligendi illum rerum omnis porro ex, magni, explicabo 
				veniam incidunt in quam sapiente ut ipsum.</p>
				<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel 
				exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi 
				dolores. Sequi itaque, unde perferendis nemo debitis dolor.</p>
			</div>
			<div class="col-sm-5">
				<div class="img-about img img-blue"></div>
			</div>
		</div>
	</div>
</section>
```
```css
.h2 {
	@extend .h1;
	margin-bottom: 30px;
	color: #445161;
	font-size: 30px;
	line-height: 36px;
}

.img {
	............
	&-about {
		height: 245px;
	}
}
```
Заголовок .h2 наследует все css свойства кроме цвета, размер шрифта и высоты линии.

### Секция Plusses
```html
<section class="section section-plusses section-gray">
	<div class="container">
		<div class="row">
			<div class="cols-sm-12">
				<h2 class="h2 text-center">Dignity and pluses product</h2>
			</div>
			<div class="col-sm-6">
				<ul class="list list-plusses">
					<li>Delectus dolorem vero quae beatae quasi dolor deserunt iste amet atque, impedit iure placeat, ullam. Reprehenderit aliquam, nemo cum velit ratione perferendis quas, maxime, quaerat porro totam, dolore minus inventore.</li>
					<li>Delectus dolorem vero quae beatae quasi dolor deserunt iste amet atque, impedit iure placeat, ullam. Reprehenderit aliquam, nemo cum velit ratione perferendis quas, maxime, quaerat porro totam, dolore minus inventore.</li>
				</ul>
			</div>
			<div class="col-sm-6">
				<ul class="list list-plusses">
					<li>Delectus dolorem vero quae beatae quasi dolor deserunt iste amet atque, impedit iure placeat, ullam. Reprehenderit aliquam, nemo cum velit ratione perferendis quas, maxime, quaerat porro totam, dolore minus inventore.</li>
					<li>Delectus dolorem vero quae beatae quasi dolor deserunt iste amet atque, impedit iure placeat, ullam. Reprehenderit aliquam, nemo cum velit ratione perferendis quas, maxime, quaerat porro totam, dolore minus inventore.</li>
				</ul>
			</div>
		</div>
	</div>
</section>
```
Заголовку h2 добавляем класс **text-center**, который будет центрировать текст любого тега к которому будет добавлен. 
```css
.text-center {
	text-align: center;
}

.section {
	............
	&-gray {
		background-color: #f5f5f5;
	}
}

.list {
	............
	&-plusses {
		li {
			margin-bottom: 30px;
			padding-left: 42px; 
			position: relative;
			&::before {
				content: '';
				position: absolute;
				top: 4px;
				left: 0;
				width: 32px;
				height: 32px;
				background-image: url('../img/plus-icon.jpg');
			}
		}
	}
}
```
Здесь мы экспортировали иконку списка и назвали его **plus-icon.jpg**. При подключении иконки, мы позицинируюм top: 4px, так как из-за высоты линии текстка, иконка находилась выше. Так как некоторые секции имеет серый фон, добавили класс **section-gray**, для управления серым фоном секций. 

### Секция Screenshots
```html
<section class="section section-screenshots">
	<div class="container">
		<div class="row">
			<div class="col-sm-12">
				<h2 class="h2 text-center">Screenshots</h2>
			</div>

			<div class="col-sm-6">
				<ul class="list list-screenshots">
					<li>
						<div class="img img-blue img-screenshots"></div>
						<div class="list-screenshots-content">
							<h3 class="h3">The description for the image</h3>
							<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi dolores. Sequi itaque, unde perferendis nemo debitis</p>
						</div>
					</li>
					<li>
						<div class="img img-blue img-screenshots"></div>
						<div class="list-screenshots-content">
							<h3 class="h3">The description for the image</h3>
							<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi dolores. Sequi itaque, unde perferendis nemo debitis</p>
						</div>
					</li>
				</ul>
			</div>

			<div class="col-sm-6">
				<ul class="list list-screenshots">
					<li>
						<div class="img img-blue img-screenshots"></div>
						<div class="list-screenshots-content">
							<h3 class="h3">The description for the image</h3>
							<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi dolores. Sequi itaque, unde perferendis nemo debitis</p>
						</div>
					</li>
					<li>
						<div class="img img-blue img-screenshots"></div>
						<div class="list-screenshots-content">
							<h3 class="h3">The description for the image</h3>
							<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi dolores. Sequi itaque, unde perferendis nemo debitis</p>
						</div>
					</li>
				</ul>
			</div>					
		</div>
	</div>
</section>
```
```css
.h3 {
	@extend .h2;
	margin-bottom: 15px;
	font-size: 22px;
	line-height: 30px;
}

.list {
	............
	&-screenshots {
		li {
			margin-bottom: 30px;
		}
	}
}

.img {
	............
	&-screenshots {
		width: 140px;
		height: 140px;
		float: left;
		margin-right: 20px;
	}
}
```
Все размеры ширины, высоты и отступы измеряем в макете. 

### Секция Reviews
```html
<section class="section section-reviews section-gray">
	<div class="container">
		<div class="row">
			<div class="col-sm-12">
				<h2 class="h2 text-center">Reviews</h2>
			</div>

			<div class="col-sm-6">
				<ul class="list list-reviews">
					<li>
						<div class="img img-blue img-reviews"></div>
						<div class="list-reviews-content">
							<p>Porro officia cumque sint deleniti nemo facere rem vitae odit inventore cum odio, iste quia doloribus autem aperiam nulla ea neque reprehenderit. Libero doloribus, possimus officiis sapiente necessitatibus commodi consectetur?</p>
							<p class="review-author">Lourens S.</p>
						</div>
					</li>
					<li>
						<div class="img img-blue img-reviews"></div>
						<div class="list-reviews-content">
							<p>Porro officia cumque sint deleniti nemo facere rem vitae odit inventore cum odio, iste quia doloribus autem aperiam nulla ea neque reprehenderit. Libero doloribus, possimus officiis sapiente necessitatibus commodi consectetur?</p>
							<p class="review-author">Lourens S.</p>
						</div>
					</li>
				</ul>
			</div>

			<div class="col-sm-6">
				<ul class="list list-reviews">
					<li>
						<div class="img img-blue img-reviews"></div>
						<div class="list-reviews-content">
							<p>Porro officia cumque sint deleniti nemo facere rem vitae odit inventore cum odio, iste quia doloribus autem aperiam nulla ea neque reprehenderit. Libero doloribus, possimus officiis sapiente necessitatibus commodi consectetur?</p>
							<p class="review-author">Lourens S.</p>
						</div>
					</li>
					<li>
						<div class="img img-blue img-reviews"></div>
						<div class="list-reviews-content">
							<p>Porro officia cumque sint deleniti nemo facere rem vitae odit inventore cum odio, iste quia doloribus autem aperiam nulla ea neque reprehenderit. Libero doloribus, possimus officiis sapiente necessitatibus commodi consectetur?</p>
							<p class="review-author">Lourens S.</p>
						</div>
					</li>
				</ul>
			</div>
		</div>
	</div>
</section>
```

```css
.list {
	............
	&-reviews {
		li {
			display: flex;
			margin-bottom: 25px;

			p {
				font-size: 14px;
				line-height: 18px;
				font-style: italic;
				margin: 0;

				&.review-author {
					margin-top: 5px;
					color: #989898;
				}
			}
		}

		&-content {
			background-color: #ebebeb;
			padding: 15px 20px;
			border-radius: 5px;
			position: relative;

			&::before {
				content: '';
				position: absolute;
				top: 25.5px;
				left: -24px;
				border: 12px solid transparent;
				border-right-color: #ebebeb;
			}
		}
	}
}

.img {
	............
	&-reviews {
		width: 75px;
		height: 75px;
		border-radius: 50%;
		flex-grow: 0;
		flex-shrink: 0;
		margin-right: 25px;
	}
}
```
