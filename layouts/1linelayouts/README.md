# 1-Line Layouts*

*10 Modern CSS layout and sizing techniques that highlight just how robust and impactful a single-line of styling code can be.

**10 современных раскладок в одну строку CSS-кода**

Примеры [к статье](https://1linelayouts.glitch.me/) и сама статья. | [Статья на Хабре](https://habr.com/ru/articles/522880/) | Автор оригинала: [Una Kravets](https://web.dev/authors/una) | Видео от автора [на YouTube](https://www.youtube.com/watch?v=qm0IfG1GyZU)

Все примеры в [одном файле](./index.html).

## 1. Super Centered / Суперцентрирование: place-items: center

[Перейти к примеру](./super-centered/index.html) | [Посмотреть на CodePen](https://codepen.io/dzmuh/pen/WNVoOgO)

В первом примере "однострочной" раскладки давайте решим самую главную загадку во всём CSS: центрирование. Хочу, чтобы вы знали, что 'place-items: center' это проще, чем кажется.

Сначала задайте родительскому элементу свойству display со значением grid, а затем для него же place-items: center. Свойство place-items это краткая форма записи для align-items и justify-items, с помощью которого мы устанавливаем оба эти свойства в значение center.

```css
.parent {
    display: grid;
    place-items: center;
}
```

Данный способ приводит к идеальному центрированию содержимого внутри родителя, независимо от его размера.

## 2. The Deconstructed Pancake / Адаптивные блоки: flex: \<grow\> \<shrink\> \<baseWidth\>

[Перейти к примеру](./deconstructed-pancake/index.html) | [Посмотреть на CodePen](https://codepen.io/dzmuh/pen/eYqBRoL)

Это распространённая раскладка, например, для лендингов, в которой может располагаться ряд из 3 элементов, обычно содержащих изображение, заголовок и текст, описывающих особенности продукта. Но мы хотим, чтобы эти элементы также аккуратно располагались и при просмотре страницы с мобильных устройств.

Если использовать Flexbox, вам не придётся настраивать расположение элементов для разных размеров экрана с помощью медиа-запросов.

Свойство [flex](https://developer.mozilla.org/en-US/docs/Web/CSS/flex) является сокращением и позволяет задать набор значений `flex: <flex-grow> <flex-shrink> <flex-basis>`

Если нужно, чтобы блоки имели `<flex-basis>` размер, сжимались на меньших размерах, но не увеличивались для заполнения дополнительного свободного пространства, следует указать `flex: 0 1 <flex-basis>`. В данном случае `<flex-basis>` равно 150px. Код будет следующим:

```css
.parent {
  display: flex;
}

.child {
  flex: 0 1 150px;
}
```

Если вы хотите, чтобы при переносе на новую строку блоки растягивали и заполняли пространство, установите `<flex-grow>` в значение 1.

```css
.parent {
  display: flex;
}

.child {
  flex: 1 1 150px;
}
```

Теперь при изменении размера экрана Flex-элементы будут и сужаться и увеличиваться в размере.

## 3. Sidebar Says / Боковая панель: grid-template-columns: minmax(\<min\>, \<max\>) 1fr)

[Перейти к примеру](./deconstructed-pancake/index.html) | [Посмотреть на CodePen](https://codepen.io/dzmuh/pen/eYqBaqv)

В этой демонстрации используется преимущество функции [minmax](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax) для grid-раскладки. Мы устанавливаем минимальный размер боковой панели равным `150px`, но на экранах бо́льшей ширины позволяем растягиваться на `25%`. Таким образом, панель будет занимать `25%` ширины родителя, пока эти `25%` не станут меньше `150px`.

Укажем эту функцию в значении свойства `grid-template-columns`. Элемент в первой колонке (в нашем случае это боковая панель) получает `minmax` между `150px` и `25%`, а второй элемент (в нашем случае это `main`) занимает оставшееся пространство `1fr`.

```css
.parent {
    display: grid;
    grid-template-columns: minmax(150px, 25%) 1fr;
}
```
