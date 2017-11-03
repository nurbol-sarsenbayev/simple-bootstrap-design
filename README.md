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
	<section class="section section-plusses section-gray"></section>
	<section class="section section-screenshots"></section>
	<section class="section section-reviews section-gray"></section>
	<section class="section section-prices"></section>
	<section class="section section-contacts section-inverse"></section>
	<footer  class="section-gray page-footer"></footer>
</div>
```
Будет один блок **page-wrapper** в котором будет все секции макета и header, footer. Классы секций будет начинаться так **section section-**, чтобы выделить от остальных классов. **section-inverse** означает, что это секция будеть иметь синий фон с белым текстом, когда обычная секция имеет белый фон и черный текст по макету. Есть еще некоторые секции серым фоном, где указаны классом **section-gray**.  Все основные css коды пишем в **app/sass/main.scss**. 
```css
.section {
	padding: 50px 0;
	background-color: #fff;

	&-inverse {
		background-color: $accent;
		color: #fff;
	}

	&-gray {
		background-color: #f5f5f5;
	}
}
```
Здесь `$accent` переменнаю, которую мы указываем с отальными переменнами в **app/sass/_vars.scss**:
```scss
$accent: #445162;
$default-font: Arial, sans-serif;
$default_text_color: #333;
$default_font_size: 16px;
$default_line_height: 24px;
```
Его значение это цвет, который встречается чаще в макете. Остальные это параметры текста, которых определим выбирая основные тексты и смотря какие у них параметры в окне Character в фотошопе:
![Текст в Фотошопе](https://nurbol-sarsenbayev.github.io/images/simple-bootstrap-design/photoshop_character.JPG)
На рисунке видно, что шрифт (font-family) Arial, размер шрифта (font-size) 16px, высота линии (line-height) 24px, цвет текста (color) черный. Чтобы эти свойствы были заданы на все элементы, а не только к тексту, их пишем в body:
```css
body {
	min-width: 320px;
	position: relative;
	line-height: $default_line_height;
	font-size: $default_font_size;
	font-family: $default-font;
	color: $default_text_color;
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
			<div class="col-sm-5 col-sm-push-7">
				<div class="img-header img img-white"></div>
			</div>							
			<div class="col-sm-7 col-sm-pull-5">
				<h1 class="h1">Product name</h1>
				<ul class="list list-header">
					<li>Put on this page information about your product</li>
					<li>A detailed description of your product</li>
					<li>Tell us about the advantages and merits</li>
					<li>Associate the page with the payment system</li>
				</ul>
			</div>
		</div>
	</div>
</header>
```
Столбцы имеет такие классы **col-sm-5 col-sm-push-7** и **col-sm-7 col-sm-pull-5**, чтобы на маленьких экранах столбец с рисунком (col-sm-5) находился на верху, а на сердних и больших экранах расположился в правой стороне. 
CSS шапка:
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
В макета высота линии заголовка задан auto, а это значить нам придется задать примерную высоту линию. Лучшии практики будет написать css свойствы на классы, а не на семантические теги, поэтому css коды пишем на .h1 класс, а не на h1. А иконка в макете сделан как рисунок, но в 2017 году иконок в основном делает через шрифт fontawesome. Так как иконка рисунок, мы дадим примерную размер шрифта иконка. Класс списка написан так **class="list list-header"**, чтобы css свйоства списков осталных секций написать в одном месте.  
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
При изменении размера экрана, необходимо будет изменить некоторые css свойства. Эти изменения пишеться в **app/sass/_media.scss*:
```scss
@media only screen and (max-width : 768px) {
	.section {
		&-header {
			.h1 {
				text-align: center;
				margin-top: 10px;
				font-size: 50px;
			}

			.list-header {
				margin: 0;
			}
		}	
	}
}
```
В макете, нет инструкцию, что делать в дизайном в маленьких экранах. Поэтому css свойства изменены по моему усматрению. 

### Секция About
```html
<section class="section section-about">
	<div class="container">
		<div class="row">
			<div class="col-sm-5 col-sm-push-7">
				<div class="img-about img img-blue"></div>
			</div>
			<div class="col-sm-7 col-sm-pull-5">
				<h2 class="h2">About your product</h2>
				<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis facilis fuga, 
					illo at. Natus eos, eligendi illum rerum omnis porro ex, magni, explicabo 
					veniam incidunt in quam sapiente ut ipsum.</p>
				<p>Pariatur iure ab sunt nesciunt, quibusdam odio iste cumque itaque, ipsa vel 
					exercitationem ullam quos aut nostrum cupiditate fuga quaerat quam animi 
					dolores. Sequi itaque, unde perferendis nemo debitis dolor.</p>
			</div>
		</div>
	</div>
</section>
```
Столбцы, точно такие же как в header. 
```css
.h2 {
	@extend .h1;
	margin-bottom: 30px;
	color: $accent;
	font-size: 30px;
	line-height: 36px;
	.section-inverse & {
		color: #fff;
	}
}

.img {
	............
	&-about {
		height: 245px;
	}
}
```
Заголовок .h2 наследует все css свойства кроме цвета, размер шрифта и высоты линии и пишется отдельно от секции About, потому-что используется этот h2 как заголовок в остальных секциях тоже.
CSS в **app/sass/_media.scss**:
```scss
@media only screen and (max-width : 768px) {
	.section {
		............
		&-about {
			.h2 {
				margin: 10px 0 0 0;
				text-align: center;
			}
		}
	}
}
```

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
Здесь мы экспортировали иконку списка и назвали его **plus-icon.jpg**. При подключении иконки, мы позицинируюм top: 4px, так как из-за высоты линии текстка, иконка находилась выше.  

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
	<div class="container-fluid">
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
Блок классом **container** заменем на **container-fluid**, так как это секция расположен на всю ширину экрана. А внутрений отступ (padding) этой секции по горизанталю будет иметь относительную значению (%, а не px). 
```css
.section {
	............
	&-reviews {
		padding-left: 3%;
		padding-right: 3%;
	}
}

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
Сделаем элемент списка _flex_ для того чтобы рисунок и контент находился в одной строке. После этого рисунку задаем css `flex-grow: 0; flex-shrink: 0;`, после которого при изменении экрана размер рисунка не будет меняться. border-radius блока **.list-reviews-content** дал примерную значению, из-за невозможности измерить в макете. А top позицию его псевдоэлемента before вычислил так: `75px/2 - 12px`, где 75px это высота рисунка, а 12px это рамка псевдоэлемента before. 
Если размер экрана будет меньше чем 768px, тогда отступы этой секции будет больше чем у остальных секции, и будет занимать полезное место, в котором мог расположится контент. Чтобы избежать этого, в **app/sass/media.scss** пишем: 
```css
@media only screen and (max-width : 768px) {
	.section {
		............
		&-reviews {
			padding-left: 0;
			padding-right: 0;
		}
	}
}
```

### Секция Prices
```html
<section class="section section-prices">
	<div class="container">
		<div class="row">
			<div class="col-sm-12">
				<h2 class="h2 text-center">Buy it now</h2>

				<div class="prices">								
					<div class="prices-item">
						<h4 class="prices-title">Standart</h4>
						<div class="prices-price">$100</div>
						<div class="prices-content">
							<ol class="prices-list">
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>								
							</ol>
							<button class="button prices-button">Buy</button>
						</div>
					</div>

					<div class="prices-item">
						<h4 class="prices-title">Premium</h4>
						<div class="prices-price">$150</div>
						<div class="prices-content">
							<ol class="prices-list">
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>								
							</ol>
							<button class="button prices-button">Buy</button>
						</div>
					</div>

					<div class="prices-item">
						<h4 class="prices-title">Lux</h4>
						<div class="prices-price">$200</div>
						<div class="prices-content">
							<ol class="prices-list">
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>
								<li>Porro officia cumque sint deleniti;</li>
								<li>Тemo facere rem vitae odit;</li>
								<li>Cum odio, iste quia doloribus autem;</li>
								<li>Aperiam nulla ea neque;</li>
							</ol>
							<button class="button prices-button">Buy</button>	
						</div>
					</div>
				</div>	
			</div>					
		</div>
	</div>
</section>
```
В этой секции, блоки будет располагатся не через bootstrap сетку, а через css Flex, потому-что в bootstrap-е невозможно выравнять блоки по вертикали, которые имеет разные высоты. 
```css
.button {
	background-color: #ffffff;
	outline: none;
	border: 0;
	height: 40px;
	color: $accent;
	font-weight: bold;
	font-size: 18px;
	line-height: 40px;
	padding: 0 50px;
	border-radius: 5px;
}

.prices {
	display: flex;
	align-items: flex-end;
	text-align: center;

	&-item {
		background-color: $accent;
		border-radius: 5px;
		flex-grow: 1;
		
		&:nth-child(2) {
			margin: 0 20px;
		}
	}

	&-title {
		color: #ffffff;
		font-size: 24px;
		font-weight: normal;
		line-height: 50px;
		height: 50px;
		margin: 0;
	}

	&-price {
		color: $accent;
		background-color: #ffffff;
		height: 68px;
		line-height: 68px;
		font-size: 40px;
		margin: 0 2px;
	}

	&-content {
		padding: 20px;
	}

	&-list {
		color: #fff;
		font-size: 14px;
		line-height: 24px;
		text-align: left;
		padding: 0;
		margin: 0 0 20px;
		list-style-position: inside;
	}

	&-button {
		padding: 0;
		width: 100%;
	}
}
```
Класс **.button** отдельно размещался, потому-что есть еще кнопка в секции Contacts, которая имеет очень схожый вид. Блок .prices имеет css свойства `display: flex; align-items: flex-end;` для того, чтобы его элементы расположились по горизонталю в одной линии, а по вертикали в нижней части блока. А элементы блока (.prices-item) имеет `flex-grow: 1;`, чтобы занимать весь контент по горизонталю (ширина элементов резиновая). 
CSS в **app/sass/_media.scss*:
```scss
@media only screen and (max-width : 768px) {
	.section {
		............
		&-prices {
			.prices {
				display: block;

				&-item:nth-child(2) {
					margin: 20px 0;
				}
			}
		}
	}
}
```

### Секция Contacts
```html
<section class="section section-contacts section-inverse">
	<div class="container">
		<div class="row">
			<div class="col-sm-12">
				<h2 class="h2 text-center">Contacts</h2>
			</div>

			<div class="col-sm-6 col-sm-offset-1">
				<input type="text" class="input" placeholder="Your name:">
				<input type="email" class="input" placeholder="Your email:">
				<textarea class="textarea" placeholder="Your message:"></textarea>
				<div class="text-center">
					<button class="button">Send</button>
				</div>
			</div>

			<div class="col-sm-4 col-sm-offset-1">
				<p><i class="fa fa-skype"></i>here_your_login_skype</p>
				<p><i class="fa fa-whatsapp"></i>279679659</p>
				<p><i class="fa fa-envelope-o"></i>psdhtmlcss@mail.ru</p>
				<p><i class="fa fa-phone"></i>80 00 4568 55 55</p>

				<div>
					<a href="#" class="contact-social-btn"><i class="fa fa-twitter"></i></a>
					<a href="#" class="contact-social-btn"><i class="fa fa-facebook"></i></a>
					<a href="#" class="contact-social-btn"><i class="fa fa-instagram"></i></a>
					<a href="#" class="contact-social-btn"><i class="fa fa-google"></i></a>
					<a href="#" class="contact-social-btn"><i class="fa fa-youtube"></i></a>
				</div>
			</div>
		</div>
	</div>
</section>
```
Класс **col-sm-offset-1** используется, для того чтобы переместить столбец в лево в одну колонку. Иконок icq и @ поменяли, так как их не было в шрифте fontawesome. А некоторые социалные иконки выглядит по другому. 
```scss
.input {
	border: 0;
	outline: 0;
	background-color: #ffffff;
	color: $accent;
	height: 40px;
	line-height: 40px;
	padding: 0 20px;
	display: block;	
	width: 100%;
	border-radius: 5px;
	font-size: 16px;

	&::-webkit-input-placeholder {
		color: $accent;
		font-family: Arial, sans-serif;
		opacity: 1;
	}
		
	&::-moz-placeholder {
		color: $accent;
		opacity: 1;
	}
	
	&:-ms-input-placeholder {
		color: $accent;
		opacity: 1;
	}		
}

.textarea {
	@extend .input;
	height: 170px;
	line-height: 24px;
	padding-top: 5px;
	padding-bottom: 5px;
}

.section {
	............
	&-contacts {
		.input {
			margin-bottom: 20px;
		}

		.button {
			margin: 0 auto;
		}

		p {
			position: relative;
			padding-left: 34px;
			margin: 0 0 30px 0;
			.fa {
				font-size: 26px;
				position: absolute;
				top: 50%;
				left: 0;
				transform: translateY(-50%);
			}
		}

		.contact-social-btn {
			width: 40px;
			height: 40px;
			background-color: #ffffff;
			display: inline-block;
			font-size: 26px;
			line-height: 40px;
			text-align: center;
			border-radius: 50%;
			color: $accent;
			margin-right: 3px;
		}
	}
}
```

### Секция Footer
```html
<footer class="section-gray page-footer">
	<div class="container">
		<p class="text-center">Copyright © 2014 Product name · PSD HTML CSS</p>
	</div>
</footer>
```

```scss
.page-footer {
	color: $accent;
	font-size: 12px;
	line-height: 24px;

	p {
		margin: 2px 0;
	}
}
```
