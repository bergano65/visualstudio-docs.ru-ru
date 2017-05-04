---
title: "Свойства 0...n (arguments) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "свойства 0...n"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Свойства 0...n (arguments) (JavaScript)
Возвращает фактическое значение отдельных аргументов из объекта **arguments**, который возвращается свойством **arguments** выполняемой функции.  
  
## Синтаксис  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## Параметры  
 *function*  
 Необязательный.  Имя объекта `Function`, выполняемого в данный момент.  
  
 0, 1, 2, *, n*  
 Обязательный.  Неотрицательное целое число в диапазоне от 0 до значения *n*, где 0 представляет первый аргумент, а *n* представляет последний аргумент.  Значение последнего аргумента *n* равно **arguments.length\-1**.  
  
## Заметки  
 Значения, возвращаемые 0.  .  .  Свойства n — фактические значения, передаваемые в выполняемую функцию.  Доступ к отдельным аргументам, составляющим объект **arguments**, которые фактически не являются массивом аргументов, осуществляется тем же способом, что и к элементам массива.  
  
## Пример  
 В следующем примере демонстрируется использование **0. . . Свойства**  ***n*** объекта **arguments**.  Для полного понимания примера следует передать функции один или несколько аргументов.  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Объект Function](../../javascript/reference/function-object-javascript.md)  
  
## См. также  
 [Свойство length \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Свойство length \(функция\)](../../javascript/reference/length-property-function-javascript.md)