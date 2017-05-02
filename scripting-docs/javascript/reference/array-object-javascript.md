---
title: "Объект Array (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Array"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array - объект"
  - "constructor - свойство"
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Объект Array (JavaScript)
Поддерживает создание массивов любого типа данных.  
  
## Синтаксис  
  
```  
  
        arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Имя переменной, которой присваивается объект `Array`.  
  
 `size`  
 Необязательный.  Размер массива.  Поскольку массивы отсчитываются от нуля, созданным элементам присваиваются индексы от нуля до `size` –1.  
  
 `element0,...,elementN`  
 Необязательный.  Элементы, которые нужно поместить в массив.  Создает массив с числом элементов *n* \+ 1 и значением `length`, равным *n* \+ 1.  При использовании данного синтаксиса необходимо указывать более одного элемента.  
  
## Заметки  
 Для получения доступа к отдельным элементам созданного массива используется нотация "\[ \]".  Обратите внимание, что массивы в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отсчитываются от нуля.  
  
```javascript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Чтобы указать размер массива, можно передать в конструктор `Array` 32\-разрядное целое число без знака.  Если значение является отрицательным или не является целым числом, возникает ошибка времени выполнения.  Если вы запустите следующий код, эта ошибка отобразится в консоли:  
  
```javascript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Если в конструктор `Array` передается одно значение, не являющееся числом, свойство `length` получает значение 1, а значение единственного элемента становится единственным передаваемым аргументом.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Массивы JavaScript являются разреженными, то есть некоторые элементы массива могут не содержать данных.  В JavaScript в массиве существуют только те элементы, которые действительно содержат данные.  Это позволяет сократить объем памяти, используемой массивом.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Некоторые члены из следующих списков были представлены в более поздних версиях.  Дополнительные сведения см. в статье [Сведения о версии](../../javascript/reference/javascript-version-information.md) или в документации по отдельным членам.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Array`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-array.md)|Указывает функцию, которая создает массив.|  
|[Свойство length \(Array\)](../../javascript/reference/length-property-array-javascript.md)|Возвращает целочисленное значение, которое на единицу больше индекса последнего определенного элемента массива.|  
|[Свойство prototype](../../javascript/reference/prototype-property-array.md)|Возвращает ссылку на прототип массива.|  
  
## Функции  
 В следующей таблице описаны функции объекта `Array`.  
  
|Функция|Описание|  
|-------------|--------------|  
|[Функция Array.from](../../javascript/reference/array-from-function-array-javascript.md)|Возвращает массив из итерируемого объекта или объекта, имеющего вид массива.|  
|[Функция Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Возвращает логическое значение, указывающее, является ли объект массивом.|  
|[Функция Array.of](../../javascript/reference/array-of-function-array-javascript.md)|Возвращает массив из переданных аргументов.|  
  
<a name="js56jsobjarraymeth"></a>   
## Методы  
 В следующей таблице перечислены методы объекта `Array`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод concat \(Array\)](../../javascript/reference/concat-method-array-javascript.md)|Возвращает новый массив, состоящий из объединения двух массивов.|  
|[Метод entries](../../javascript/reference/entries-method-array-javascript.md)|Возвращает итератор, который содержит пары "ключ\- значение" массива.|  
|[Метод every](../../javascript/reference/every-method-array-javascript.md)|Проверяет, возвращает ли указанная функция обратного вызова `true` для всех элементов массива.|  
|[Метод fill](../../javascript/reference/fill-method-array-javascript.md)|Заполняет массив указанным значением.|  
|[Метод filter](../../javascript/reference/filter-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива и возвращает массив значений, для которых она возвращает `true`.|  
|[Метод findIndex](../../javascript/reference/findindex-method-array-javascript.md)|Возвращает значение индекса для первого элемента массива, который соответствует тестовым критериям, указанным в функции обратного вызова.|  
|[Метод forEach](../../javascript/reference/foreach-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод indexOf \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)|Возвращает индекс первого вхождения значения в массиве.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в другом объекте цепочки прототипов.|  
|[Метод join](../../javascript/reference/join-method-array-javascript.md)|Возвращает объект `String`, состоящий из всех элементов массива, соединенных вместе.|  
|[Метод keys](../../javascript/reference/keys-method-array-javascript.md)|Возвращает итератор, который содержит значения индексов массива.|  
|[Метод lastIndexOf \(Array\)](../../javascript/reference/lastindexof-method-array-javascript.md)|Возвращает индекс последнего вхождения указанного значения в массиве.|  
|[Метод map](../../javascript/reference/map-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива и возвращает массив, содержащий результаты.|  
|[Метод pop](../../javascript/reference/pop-method-array-javascript.md)|Удаляет последний элемент из массива и возвращает его.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта и является ли оно перечислимым.|  
|[Метод push](../../javascript/reference/push-method-array-javascript.md)|Присоединяет новые элементы к массиву и возвращает новую длину массива.|  
|[Метод reduce](../../javascript/reference/reduce-method-array-javascript.md)|Накапливает единый результат посредством вызова заданной функции обратного вызова для всех элементов массива.  Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.|  
|[Метод reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Накапливает единый результат посредством вызова заданной функции обратного вызова для всех элементов массива в порядке убывания индекса.  Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.|  
|[Метод reverse](../../javascript/reference/reverse-method-javascript.md)|Возвращает объект `Array` с обратным порядком элементов.|  
|[Метод shift](../../javascript/reference/shift-method-array-javascript.md)|Удаляет первый элемент из массива и возвращает его.|  
|[Метод slice \(Array\)](../../javascript/reference/slice-method-array-javascript.md)|Возвращает фрагмент массива.|  
|[Метод some](../../javascript/reference/some-method-array-javascript.md)|Проверяет, возвращает ли заданная функция обратного вызова значение `true` для какого\-либо элемента массива.|  
|[Метод sort](../../javascript/reference/sort-method-array-javascript.md)|Возвращает объект `Array` с упорядоченными элементами.|  
|[Метод splice](../../javascript/reference/splice-method-array-javascript.md)|Удаляет элементы из массива и при необходимости вставляет на их место новые элементы, возвращая удаленные элементы.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Возвращает строку с использованием текущего языкового стандарта.|  
|[Метод toString](../../javascript/reference/tostring-method-array.md)|Возвращает строковое представление массива.|  
|[Метод unshift](../../javascript/reference/unshift-method-array-javascript.md)|Вставляет новые элементы в начало массива.|  
|[Метод valueOf](../../javascript/reference/valueof-method-array.md)|Получает ссылку на массив.|  
|[Метод values](../../javascript/reference/values-method-array-javascript.md)|Возвращает итератор, который содержит значения массива.|  
  
## См. также  
 [Пример приложения с функциями прокрутки, сдвига и масштабирования](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)