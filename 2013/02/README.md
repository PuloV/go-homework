# Images

За следващата задача се налага да поработим с изображения (за Vim-аджиите си намерете afterimage.vim). За целта се налага да напишете функция, която приема chunk от входящи данни за изображението (byte array) и описателна структура (header). Вашата задача ще бъде да прочетете данните, да ги нормализирате и да предоставяте достъп до тях.

##Byte array

В списъка с байтове ще се съхраняват данните за всеки пиксел от изображението.

##Header

Структурата Header, която ще носи данните за подаденото изображение, ще има данни като:

- `Format`		пази формата: RGB, RGBA, BGRA и тн.
- `LineWidth`		съдържа броя колони от пиксели

##Colors

Относно стуктурата на цветовете:
В byte масива цветовете ще ви бъдат подадени като число от 0 - 255.
Представяйте за данни всеки цвят (Red, Green, Blue, Alpha) като число между 0 и 1. Това улеснява манипулации върху тях.

##Precomputing

Процеса на нормализация се използва тип `AlphaBlend` (може да се поинтересувате, ако ви е интересно) и протича по следния начин:

За да се преизчисли интензитета на цветовете, се налага всеки цвят в даден пиксел да се умножи по стойността на алфата.

##Описание

Задачата ви е да може вашата функция да приема голям набор от различно описани (по-горе) данни и да връща стуктура Image, която да има метод `InspectPixel`.
При извикване на `InspectPixel` той трябва да връща тип Pixel, който да има Color, съдържащ Red, Green и Blue като стойности от 0 - 255.

##Пример

    >>> data := []byte{0, 12, 244, 13, 26, 52, 31, 33, 41}
    [0 12 244 13 26 52 31 33 41]
    >>> header := Header{"RGB", 3, nil}
    >>> pixel = ParseImage(data, header).InspectPixel(0, 0)
    >>> fmt.Println(pixel.Color())
    Red: 0, Green: 12, Blue: 244
