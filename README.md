# Лабораторная работа №2. Основы верстки
- _Выполнила:_ Кукарских Виктория ИСП-212о
- _Язык программирования:_ Java

## Приложение состоит из 4 экранов:
1. [Меню](#activity1).
2. [Экран 2](#activity2), который сверстан с использованием `LinearLayout`.
3. [Экран 3](#activity3), который сверстан с использованием `RelativeLayout`.
4. [Экран 4](#activity4).
5. 
---
### <a id="activity1"> Меню (экран 1) </a>

**_Меню состоит из 4х кнопок:_**
- **"Перейти к экрану 2"**. Нажатие на кнопку - > открытие [`SecondActivity`](#activity2)
- **"Перейти к экрану 3"**. Нажатие на кнопку -> открытие [`ThirdActivity`](#activity3)
- **"Перейти к экрану 4"**. Нажатие на кнопку -> открытие [`FourthActivity`](#activity4)
- **"Выйти"**. Нажатие на кнопку -> выход из приложения.

_**Верстка кнопок**_
- высота каждой кнопки составляет **20%** от высоты экрана
- расстояние между кнопками - **2%**
- ширина кнопок - **75%**
- расстояние от первой кнопки до верхнего края **==** расстоянию от последней кнопки до нижнего края **== 7%**
- кнопки выровнены по центру.

---

**Экран 2 состоит из 7 кнопок:**
- 3 расположены в верхней части экрана (`android:layout_gravity="top"`) и занимают равную ширину
- 2 расположены по центру (`android:layout_gravity="center"`), занимают равные части, но имеют отступы от краев
- 3 расположены в нижней части экрана (`android:layout_gravity="bottom"`):
    - 1 занимает половину всей ширины экрана
    - 2 делят оставшуюся часть поровну между собой

Для задания размеров и положения использовались следующие **свойства `LinearLayout`**:
- `android:layout_weight`
- `android:layout_gravity`

---

**Экран 3 остоит из 6 кнопок:**
- 2 расположены в верхней части экрана и занимают по половине экрана
- 3 расположены по центру
- 1 расположена в нижней части экрана

Для задания размеров и положения использовались следующие **свойства `RelativeLayout`**:
- _относительно родительского `RelativeLayout`_:
    - `android:layout_alignParentStart="true"` // левый верхний угол
    - `android:layout_alignParentRight="true"` // правый верхний угол
    - `android:layout_centerInParent="true"` // центр
    - `android:layout_alignParentBottom="true"` // нижняя часть
- _относительно других объектов:_
    - `android:layout_toLeftOf = "@+id/.."` // "Left 50%" и "Center_left"
    - `android:layout_toRightOf="@+id/.."` // "Right 50%" и "Center_right"

 ---

**На экране 4 расположена всего 1 кнопка. Ее особенности:**
- выровнена по центру экрана
- имеет темно-зеленый цвет
- слева от текста изображена иконка приложения
- цвет обводки кнопки `#505050`
- толщина обводки `12px` (т.к. я родилась в декабре)
- радиус скругления кнопки `24dp`
- при нажатии на кнопку ее цвет изменяется на светло-зеленый.

Для выполнения выше указанных условий был создан файл `my_button_bg` внутри папки `drawable`:
- т.к. при нажатии цвет должен изменяться, используется класс `selector`, включающий в себя 2 объекта `item` (для состояния "нажато" и "не нажато").
- каждый объект имеет одинаковую структуру:
    - ``` java
      <item android:state_focused="false"
        android:state_pressed="true" // если объект не нажат, то будет false
        android:state_enabled="true">
        <shape xmlns:android="http://schemas.android.com/apk/res/android"
        android:shape="rectangle" > // создается фигура прямоугольник
            <solid android:color="@android:color/holo_green_light" /> // указывается цвет фигуры
            <corners android:radius="24dp"/> // определяется радиус скругления
            <stroke android:width="12px" android:color="#505050" /> // задается толщина и цвет обводки
        </shape>
      </item>
      ```

Чтобы подтянулись все параметры, внутри файла с версткой экрана (`activity_fourth.xml`) указано следующее:
  - `android:background="@drawable/my_button_bg"` // фон кнопки
  - `android:drawableLeft="@drawable/ic_launcher_foreground"` // добавление иконки в левой части кнопки