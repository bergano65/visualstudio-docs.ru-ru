---
title: "Объекты и массивы (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "массивы [JavaScript]"
  - "массивы [JavaScript], объекты"
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Объекты и массивы (JavaScript)
Объекты [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] представляют собой коллекции свойств и методов.  Методом называется функция, являющаяся членом объекта.  Свойство представляет собой значение или набор значений \(в виде массива или объекта\), который является членом объекта.  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживает 4 типа объектов:  
  
-   внутренние объекты, такие как `Array` и `String`;  
  
-   создаваемые объекты;  
  
-   объекты базовой среды, такие как `window` и `document`;  
  
-   объекты ActiveX.  
  
## Свойства и методы Expando  
 Все объекты в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживают свойства и методы expando, которые могут добавляться и удаляться во время выполнения.  Эти свойства и методы могут иметь любые имена и определяться числами.  Если имя свойства или метода является простым идентификатором, оно может быть указано через точку после имени объекта, например `myObj.name`, `myObj.age` и `myObj.getAge`, как показано в следующем коде.  
  
```javascript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Если имя свойства или метода не является простым идентификатором или во время написания скрипта неизвестно, для обозначения свойства можно использовать выражение в квадратных скобках.  Перед добавлением к объекту имена всех свойств expando в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] преобразуются в строки.  
  
```javascript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Дополнительные сведения о создании объекта из определения см. в разделе [Создание объектов](../javascript/creating-objects-javascript.md).  
  
## Массивы как объекты  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] объекты и массивы обрабатываются практически одинаково, поскольку массивы — это просто особый тип объекта.  И объекты, и массивы могут иметь свойства и методы.  
  
 В отличие от объектов, массивы имеют свойство `length`.  При присвоении значения элементу массива, индекс которого больше его длины \(например, `myArray[100] = "hello"`\), значение свойства `length` автоматически увеличивается до новой длины.  Аналогично, при уменьшении значения свойства `length` любой элемент с индексом за пределами длины массива удаляется.  
  
```javascript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Массивы предоставляют методы для перебора членов и манипулирования ими.  В следующем примере показано получение свойств объектов, хранящихся в массиве.  
  
```javascript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## Многомерные массивы  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] непосредственно не поддерживает многомерные массивы, но поведение многомерных массивов можно получить, сохранив их в элементах другого массива. \(В элементах массива можно сохранять любые данные, включая другие массивы.\) Например, в следующем коде создается таблица умножения чисел до 5.  
  
```javascript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```