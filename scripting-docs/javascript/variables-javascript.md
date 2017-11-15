---
title: "Переменные (JavaScript) | Документы Майкрософт"
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="variables-javascript"></a>Переменные (JavaScript)
В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] переменная содержит значение, например "hello" или 5. Используя переменную, разработчик ссылается на данные, которые она представляет, например `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Переменные используются для хранения и извлечения значений, фигурирующих в коде, а также для работы с ними. Старайтесь присваивать переменным значащие имена, чтобы другим разработчикам было легче понять, что делает написанный вами код.  
  
## <a name="declaring-variables"></a>Объявление переменных  
 Первое появление переменной в скрипте — это ее объявление. При первом упоминании переменной она создается в памяти, что позволяет ссылаться на нее далее в скрипте. Объявлять переменные необходимо перед их использованием. Это делается с помощью ключевого слова `var`.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Если не инициализировать переменную в операторе `var`, ей автоматически присваивается значение `undefined`.  
  
## <a name="naming-variables"></a>Именование переменных  
 В языке [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] учитывается регистр символов. Это значит, что имя переменной **myCounter** отличается от имени переменной **MYCounter**. Имена переменных могут быть любой длины. Ниже приведены правила создания допустимых имен переменных.  
  
-   Первый символ должен быть буквой ASCII (в верхнем или нижнем регистре) или символом подчеркивания (_). Обратите внимание, что в качестве первого символа нельзя использовать число.  
  
-   Последующие символы должны быть буквами, числами или символами подчеркивания (_).  
  
-   Имя переменной не должно быть [зарезервированным словом](../javascript/reference/javascript-reserved-words.md).  
  
 Ниже приведено несколько примеров допустимых имен переменных:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Ниже приведено несколько примеров недопустимых имен переменных:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Если требуется объявить переменную и инициализировать ее, однако не требуется присваивать ей какое-либо определенное значение, присвойте ей значение `null`. Пример.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 При объявлении переменной без присвоения ей значения она имеет значение `undefined`. Пример.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 Значение `null` ведет себя как число 0, тогда как `undefined` ведет себя как специальное значение `NaN` (не число). Если сравнить значение `null` и значение `undefined`, они окажутся равны.  
  
 Можно объявить переменную без использования в объявлении ключевого слова `var` и присвоить ей значение. Это называется неявным преобразованием.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Использовать переменную, которая не была объявлена, невозможно.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Приведение  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] является слабо типизированным языком, в отличие от строго типизированных языков, таких как C++. Это означает, что переменные JavaScript не имеют предопределенного типа. Вместо этого типом переменной является тип ее значения. Это поведение позволяет обрабатывать значение так, как будто оно имеет иной тип.  
  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] можно выполнять операции со значениями разных типов без возникновения исключений. Интерпретатор [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] выполняет неявное преобразование типов данных — *приводит* один из типов данных к другому, а затем выполняет операцию. Правила приведения строковых, числовых и логических значений следующие:  
  
-   при сложении числа и строки число приводится к строке;  
  
-   при сложении логического значения и строки логическое значение приводится к строке;  
  
-   при сложении числа и логического значения логическое значение приводится к числу.  
  
 В следующем примере результатом сложения числа и строки является строка.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Строки автоматически преобразуются в эквивалентные числа в целях сравнения. Для явного преобразования строки в целое число используется [функция parseInt](../javascript/reference/parseint-function-javascript.md). Для явного преобразования строки в число используется [функция parseFloat](../javascript/reference/parsefloat-function-javascript.md).