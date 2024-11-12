<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# Советы профессионалов CSS [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Коллекция советов, которые помогут вам стать лучше в CSS.

> Вы найдете больше [классных списков](https://github.com/sindresorhus/awesome/) под кураторством [@sindresorhus](https://github.com/sindresorhus/).


<div id="table-of-contents"></div>

## Содержание

* [Профессиональные советы](#Профессиональные-советы)
* [Поддержка](#Поддержка)
* [Помощь проекту](../../CONTRIBUTING.md)


## Профессиональные советы

1. [Используйте CSS Reset](#Используйте-css-reset)
1. [Наследуйте `box-sizing`](#Наследуйте-box-sizing)
1. [Используйте `unset` вместо сброса всех свойств](#Используйте-unset-вместо-сброса-всех-свойств)
1. [Используйте `:not()` для добавления / удаления границ в меню навигации](#Используйте-not-для-добавления--удаления-границ-в-меню-навигации)
1. [Проверьте, установлен ли шрифт локально](#проверьте,-установлен-ли-шрифт-локально)
1. [Добавьте `line-height` в `body`](#Добавьте-line-height-в-body)
1. [Установите `:focus` для элементов формы](#Установите-focus-для-элементов-формы)
1. [Выровнять все по вертикали](#Выровнять-все-по-вертикали)
1. [Списки, разделенные запятыми](#Списки-разделенные-запятыми)
1. [Выбирайте элементы с использованием отрицательных значений в `nth-child`](#Выбирайте-элементы-с-использованием-отрицательных-значений-в-nth-child)
1. [Используйте SVG для значков](#Используйте-svg-для-значков)
1. [Используйте селектор "Лоботомированная сова"](#Используйте-селектор-Лоботомированная-сова)
1. [Используйте `max-height` для ползунков на чистом CSS](#Используйте-max-height-для-ползунков-на-чистом-css)
1. [Ячейки таблицы равной ширины](#Ячейки-таблицы-равной-ширины)
1. [Используйте Flexbox вместо margin](#Используйте-flexbox-вместо-margin)
1. [Используйте селектор атрибутов для пустых ссылок](#Используйте-селектор-атрибутов-для-пустых-ссылок)
1. [Стиль "по умолчанию" для ссылок](#тиль-по-умолчанию-для-ссылокs)
1. [Блок с собственным отношением сторон](#Блок-с-собственным-отношением-сторон)
1. [Задайте стили для поломанныx изображений](#Задайте-стили-для-поломанныx-изображений)
1. [Используйте `rem` для глобальных размеров; Используйте `em` для локальных размеров](#Используйте-rem-для-глобальных-размеров-Используйте-em-для-локальных-размеров)
1. [Отключите автовоспроизведение видео с включенным звуком](#Отключите-автовоспроизведение-видео-с-включенным-звуком)
1. [Используйте `:root` для шрифтов](#Используйте-root-для-шрифтов)
1. [Установите `font-size` для элементов формы, чтобы оптимизировать просмотр на мобильных устройствах](#Установите-font-size-для-элементов-формы-чтобы-оптимизировать-просмотр-на-мобильных-устройствах)
1. [Использовать события указателя для управления событиями мыши](#Использовать-события-указателя-для-управления-событиями-мыши)
1. [Установите `display: none` на разрывы строк, используемые как интервалы](#Установите-display-none-на-разрывы-строк-используемые-как-интервалы)
1. [Используйте `:empty`, чтобы скрыть пустые HTML элементы](#Используйте-empty-чтобы-скрыть-пустые-HTML-элементы)


### Используйте CSS Reset

Сброс CSS помогает обеспечить согласованность стилей между различными браузерами и с чистого листа начать оформление элементов. Вы можете использовать CSS библиотеки сброса такие как [Normalize](http://necolas.github.io/normalize.css/) и др., или вы можете использовать более простой способ сброса:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Теперь для всех элементов свойства margin и padding будут равны нулю, а `box-sizing: border-box` позволяет указывать размеры всему блоку, а не его содержимому.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Примечание:** Если вы будете следовать совету [Наследуйте `box-sizing`](#inherit-box-sizing), то вы можете не включать свойство `box-sizing` в ваш CSS Reset.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Наследуйте `box-sizing`

Пусть `box-sizing` будет унаследован от `html`:

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

Так значительно проще изменять `box-sizing` в плагинах или других компонентах, которые задают иное поведение.

#### [Демо](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `unset` вместо сброса всех свойств

При сбросе свойств элемента нет необходимости сбросить каждое отдельное свойство:

```css
button {
  background: none;
  border: none;
  color: inherit;
  font: inherit;
  outline: none;
  padding: 0;
}
```

Вы можете указать все свойства элемента, используя сокращенное выражение `all`. Установка значения `unset` изменяет свойства элемента на их начальные значения:

```css
button {
  all: unset;
}
```

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `:not()` для добавления / удаления границ в меню навигации

Вместо того, чтобы добавлять границу...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...а затем убирать её с последнего элемента...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...используйте псевдокласс `:not()`, чтобы добавить только к нужным элементам:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Селектор CSS определяет границу так, как ее описывает человек.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Проверьте, установлен ли шрифт локально

Вы можете проверить, установлен ли шрифт локально, прежде чем извлекать его удаленно, что также является хорошим показателем производительности.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank-Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

Шляпный совет Адаму Аргайлу за то, что он поделился этим опытом и [примером](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Добавьте `line-height` в `body`

Вам вовсе не требуется добавлять свойство `line-height` к каждому `<р>`, `<h*>`, _и т.д._. по отдельности. Вместо этого добавьте его в `body`:

```css
body {
  line-height: 1.5;
}
```

Таким образом текстовые элементы легко могут наследовать свойство от `body`.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Установите `:focus` для элементов формы

Приоритетные пользователи клавиатуры полагаются на фокус, чтобы определить, где события клавиатуры идут на странице. Сделайте фокус для элементов формы выделяющимися и последовательными, а затем реализацией браузера по умолчанию:

```css
a:focus,
button:focus,
input:focus,
select:focus,
textarea:focus {
  box-shadow: none;
  outline: #000 dotted 2px;
  outline-offset: .05em;
}
```

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Выровнять все по вертикали

Нет, это не черная магия, вы действительно можете расположить элементы по центру по вертикали:

```css
html,
body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  display: -webkit-flex;
  display: flex;
}
```

...а также с помощью CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Хотите разместить по центру что-то еще? Вертикально, горизонтально...что угодно, в любое время и в любом месте? У нас есть [хорошая статья](https://css-tricks.com/centering-css-complete-guide/) которая научит всему этому.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Списки, разделенные запятыми

Сделайте список похожим на настоящий, разделенный запятыми список:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Используйте псевдокласс `:not()` чтобы не добавлять запятую к последнему пункту.

**Примечание:** Этот совет не всегда даёт лучший результат, например, могут возникнуть проблемы у экранного диктора. Да и копирование / вставка из браузера не всегда работают со сгенерированным CSS контентом. Следует быть осторожным.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Выбирайте элементы с использованием отрицательных значений в `nth-child`

Используйте отрицательные значения в `nth-child` в CSS для выбора элементов с 1 по n.

```css
li {
  display: none;
}

/* выбирает и отображает элементы с 1 по 3 */
li:nth-child(-n+3) {
  display: block;
}
```

Или, так как вы уже немного познакомились [с `:not()`](#use-not-to-applyunapply-borders-on-navigation), попробуйте:

```css
/* выберите все элементы, кроме первых 3, и покажите их */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Что же, это было довольно легко.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте SVG для значков

Нет ни одной причины, чтобы не использовать SVG для значков:

```css
.logo {
  background: url("logo.svg");
}
```

SVG хорошо масштабируется для всех разрешений и поддерживается во всех браузерах [включая IE9 и выше](http://caniuse.com/#search=svg). Так выбросите же ваши .png, .jpg или .gif-jif-что-угодно файлы.

**Примечание:** Если у вас есть кнопки, содержащие только SVG пиктограммы, и SVG не удается загрузить, то это поможет сохранить доступность кнопки:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте селектор "Лоботомированная сова"

Название, безусловно, странное, но используя универсальный селектор (`*`) с соседним селектором (`+`), мы получаем мощное правило CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

В этом примере все элементы в потоке документа, которые следуют другие элементы получат `margin-top: 1.5em`.

Более подробную информацию о селекторе "Лоботомированная сова", можно найти в [статье Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) на *A List Apart*.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `max-height` для ползунков на чистом CSS

Реализация ползунков на чистом CSS с помощью `max-height` и `overflow hidden`:

```css
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
```

При наведении элемент расширяется до значения `max-height`, а всё что не влезло, можно прокрутить.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Ячейки таблицы равной ширины

Иногда работа с таблицами приносит боль, в таких случаях попробуйте задать `table-layout: fixed` чтобы ячейки были одинаковой ширины:

```css
.calendar {
  table-layout: fixed;
}
```

Даешь макеты таблиц без боли!

#### [Демо](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте Flexbox вместо margin

При работе с пробелами между колонок вы можете избавиться от псевдоклассов `nth,` `first-` и `last-child` воспользовавшись свойством flexbox `space-between`:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Теперь пробелы между колонками будут одного размера.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте селектор атрибутов для пустых ссылок

Отображайте ссылки, когда элемент `<a>` пустой, но есть ссылка в атрибуте `href`:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Это очень удобно.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Стиль "по умолчанию" для ссылок

Добавьте для ссылок стиль "по умолчанию":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Теперь ссылки, вставленные через CMS, которые, как правило, не имеют атрибута `class`, будут иметь отличительный признак без влияния на каскад.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Блок с собственным отношением сторон

Чтобы создать блок с собственным отношением сторон, все, что вам нужно сделать, это добавить верхний или нижний padding к DIV:

```css
.container {
  height: 0;
  padding-bottom: 20%;
  position: relative;
}

.container div {
  border: 2px dashed #ddd;
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

Использование padding 20% делает высоту параллелепипеда равной 20% от его ширины. Независимо от ширины окна, дочерний DIV будет сохранять соотношение сторон (100% / 20% = 5:1).

#### [Демо](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Задайте стили для поломанныx изображений

Сделайте поломанные изображения эстетически приятнее с CSS:

```css
img {
  display: block;
  font-family: sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

Теперь добавьте правила псевдо-элементов для отображения сообщения пользователю и URL-ссылки поломаного изображения:

```css
img:before {
  content: "Упс, изображение ниже поломалось :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Подробнее об этой модели в [исходной статье](http://bitsofco.de/styling-broken-images/) [Ire Aderinokun](https://github.com/ireade/).

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `rem` для глобальных размеров; Используйте `em` для локальных размеров

После установки базового размера шрифта всего проекта (`html { font-size: 100%; }`), установите размер шрифта для текстовых элементов через `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Затем установите размер шрифта для модулей через `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Теперь каждый модуль становится разобщенным и проще в настройке, более легким в обслуживании и гибче.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Отключите автовоспроизведение видео с включенным звуком

Это отличный трюк для пользовательских стилей. Избегайте раздражения пользователя звуком из видео, которое воспроизводится автоматически при загрузке страницы. Если звук не приглушен, то не показывайте видео:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

И снова мы воспользовались помощью псевдокласса [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `:root` для шрифтов

Размер шрифта должен подстраиваться под каждый возможный размер экрана. Вы можете рассчитывать размер шрифта, основываясь на высоте и ширине экрана с помощью `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Теперь вы можете использовать единицу `root em` на основе значения, рассчитанного с помощью `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Демо](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Установите `font-size` для элементов формы, чтобы оптимизировать просмотр на мобильных устройствах

Чтобы избежать масштабирования мобильными браузерами (iOS Safari, _и др_.) элементов HTML формы, когда раскрывающийся список `<select>` нажат, добавьте  `font-size` правило селектору:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Использовать события указателя для управления событиями мыши

[События указателя](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) позволяют указать, как мышь взаимодействует с элементом, который он трогает. Чтобы отключить событие указателя по умолчанию на кнопке, например:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

Это так просто.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Установите `display: none` на разрывы строк, используемые как интервалы

Как отметил [Гарри Робертс](https://twitter.com/csswizardry/status/1170835532584235008), это может помочь пользователям CMS использовать дополнительные разрывы строк для пробелов:

```css
br + br {
  display: none;
}
```

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


### Используйте `:empty`, чтобы скрыть пустые HTML элементы

Если у вас есть HTML элементы, которые пусты, то есть их контент ещё не установлен ни CMS, ни динамической вставкой (например, `<p class="error-message"></p>`) и вам не нравится, что они занимают пространство вашего макета, используйте псевдо-класс `:empty`, чтобы скрыть их.

```css
:empty {
  display: none;
}
```

**Примечание**: Имейте в виду, что элементы с пробельными символами не считаются пустыми, например `<p class="error-message"> </p>`.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


## Поддержка

Текущие версии Chrome, Firefox, Safari, и Edge.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>