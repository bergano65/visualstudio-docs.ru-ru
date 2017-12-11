---
title: "Управление выполнением программы (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="controlling-program-flow-javascript"></a>Управление выполнением программы (JavaScript)
Обычно операторы в скрипте [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] выполняются один за другим в том порядке, в котором они записаны. Это называется последовательным выполнением. По умолчанию программа работает именно таким образом.  
  
 Альтернативой последовательному выполнению является передача программного потока в другую часть скрипта. Вместо выполнения следующего по порядку оператора может выполняться другой.  
  
 Чтобы скрипт был полезен, эта передача управления должна осуществляться логически организованно. Передача управления в программе основывается на решении, результатом которого является оператор истинности (возвращающий логическое значение **true** или **false**). Создается выражение, которое затем проверяется на наличие результата true. Это выполняется с помощью двух основных разновидностей структур программы.  
  
 Первая разновидность — структура выбора. Она используется для указания альтернативных вариантов выполнения программы, создавая точку ее разветвления (подобную развилке на дороге). В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] доступны четыре структуры выбора:  
  
-   структура единственного выбора (**if**);  
  
-   структура двойного выбора (**if/else**);  
  
-   встроенный троичный оператор `?:`;  
  
-   структура множественного выбора (`switch`).  
  
 Вторая разновидность управляющей структуры программы — структура повторения. Она используется для указания необходимости повторять действие, пока определенное условие остается истинным. Когда выполняются условия управляющего оператора (обычно после выполнения определенного числа итераций), управление передается следующему оператору за пределами структуры повторения. В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] доступны четыре структуры повторения:  
  
-   проверка выражения в начале цикла (`while`);  
  
-   проверка выражения в конце цикла (**do/while**);  
  
-   выполнение для каждого свойства объекта (**for/in**);  
  
-   повторение под управлением счетчика (**for**).  
  
 Используя вложенные и следующие друг за другом управляющие структуры выбора и повторения, можно создавать довольно сложные скрипты.  
  
 Третья форма структурированного программного потока обеспечивается обработкой исключений, которая в данном документе не рассматривается.  
  
## <a name="using-conditional-statements"></a>Использование условных операторов  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживаются условные операторы **if** и [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md). При использовании операторов **if** проверяется выполнение условия. В случае положительного результата выполняется соответствующий код [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Если условие не выполнено, выполняется альтернативный код (в операторе `if...else`). Простейшая форма оператора **if** умещается на одной строке, однако чаще всего операторы **if** и `if...else` содержат несколько строк.  
  
 Следующие примеры демонстрируют синтаксис, используемый для операторов **if** и `if...else`. В первом примере показывается простейшая форма логического условия. Оператор или блок операторов, расположенные после **if**, выполняются в том, и только в том случае, если элемент в скобках принимает значение **true** (или может быть приведен к нему).  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Условный оператор  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] также поддерживается неявная условная форма. Вместо слова **if** перед условием в ней используется знак вопроса после проверяемого условия. Определяется 2 варианта действий: для случая выполнения условия и для случая его невыполнения. Альтернативные варианты разделяются двоеточием.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Если необходимо одновременно проверить несколько условий и известно, что одно из них выполняется или не выполняется с большей вероятностью по сравнению с другими, можно использовать так называемую быструю оценку, ускоряющую выполнение скрипта. При оценке логического выражения [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] оценивает ровно столько подвыражений, сколько необходимо для получения результата.  
  
 Например, если имеется выражение "И" ((x == 123) && (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] сначала проверяет, равен ли x 123. Если нет, все выражение не может быть истинным, даже если y равен 6. Поэтому проверка значения y не выполняется, и [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] возвращает значение **false**.  
  
 Аналогично, если только одно из нескольких условий должно давать результат **true** (при использовании оператора &#124;&#124;), проверка останавливается, как только выясняется, что какое-либо условие выполняется. Это эффективно в том случае, если проверяемые условия предполагают выполнение вызовов функций или других сложных выражений. Учитывая вышесказанное, при создании выражений "ИЛИ" сначала размещайте условия, для которых выше вероятность значения **true**. При создании выражений "И" сначала размещайте условия, для которых выше вероятность значения **false**.  
  
 Преимущество этого способа создания скрипта можно увидеть в следующем примере. Здесь функция **runsecond()** не будет выполняться, если **runfirst()** возвращает значение 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Использование циклов  
 Есть несколько способов повторного выполнения оператора или блока операторов. Повторяющееся выполнение называется *циклом* или *итерацией*. Проще говоря, итерация — это однократное выполнение цикла. Для управления циклами обычно выполняется проверка переменной, значение которой изменяется при каждом выполнении цикла. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживает 4 типа циклов: циклы [for](../javascript/reference/for-statement-javascript.md), циклы [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), циклы [while](../javascript/reference/while-statement-javascript.md) и циклы [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md).  
  
## <a name="using-for-loops"></a>Использование циклов for  
 Оператор **for** указывает переменную счетчика, условие проверки и действие, обновляющее счетчик. Условие проверяется перед каждой итерацией цикла. В случае успешной проверки выполняется код внутри цикла. Если проверка не пройдена успешно, код внутри цикла не выполняется, а программа продолжает работу с первой строки, следующей непосредственно после цикла. После выполнения цикла переменная счетчика обновляется перед началом следующей итерации.  
  
 Если условие цикла не выполняется, цикл не запускается. Если условие цикла выполняется всегда, образуется бесконечный цикл. Циклы первого типа иногда бывают полезны, но бесконечные циклы используются крайне редко, поэтому будьте внимательны при определении условий цикла.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Использование циклов "for...in"  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] предусмотрен особый тип цикла для перебора всех определяемых пользователем свойств [объекта](../javascript/objects-and-arrays-javascript.md) или всех элементов массива. Счетчик цикла `for...in` представляет собой не число, а строку. Он содержит имя текущего свойства или индекс текущего элемента массива.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Хотя циклы `for...in` напоминают циклы `For Each...Next` VBScript, они действуют иначе. В цикле **for...in loop** [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] выполняется перебор свойств объектов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], а в цикле **For Each...Next** VBScript — перебор элементов коллекции. Для перебора коллекций в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] нужно использовать объект [Enumerator Object](../javascript/reference/enumerator-object-javascript.md) или метод `forEach` (если он присутствует) объекта коллекции. Хотя некоторые объекты, например в Internet Explorer, поддерживают как цикл **For Each...Next** VBScript, так и цикл **for...in** [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], большинство объектов не поддерживает оба цикла.  
  
## <a name="using-while-loops"></a>Использование циклов while  
 Цикл `while` аналогичен циклу **for**. Различие заключается в том, что в цикле `while` нет встроенной переменной счетчика и выражения обновления. Цикл `while` следует использовать, если для управления повторным выполнением оператора или блока операторов требуется более сложное правило, чем просто "выполнить код n раз". В следующем примере используется объектная модель Internet Explorer и цикл `while`, чтобы задать пользователю простой вопрос.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Так как циклы `while` не имеют явных переменных счетчика, они более подвержены бесконечной цикличности, чем другие типы циклов. Более того, поскольку положение и время обновления условия цикла не всегда просто найти, цикл `while`, в котором условие никогда не обновляется, можно написать легко. По этой причине следует проявлять осторожность при построении циклов `while`.  
  
 Как указано выше, в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] также есть цикл **do...while**, аналогичный циклу while, но отличающийся тем, что он гарантированно выполняется по меньшей мере один раз, так как условие проверяется в конце цикла, а не в начале. Например, показанный выше цикл можно переписать следующим образом:  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Использование операторов break и continue  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] оператор [break](../javascript/reference/break-statement-javascript.md) используется для остановки цикла при выполнении определенного условия. (Обратите внимание, что оператор **break** также используется для выхода из блока `switch`.) Оператор [continue](../javascript/reference/continue-statement-javascript.md) можно использовать для мгновенного перехода к следующей итерации с пропуском оставшейся части блока кода при обновлении переменной счетчика в цикле **for** или `for...in`.  
  
 Следующий пример основан на предыдущем. В нем для управления циклом используются операторы **break** и **continue**.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```