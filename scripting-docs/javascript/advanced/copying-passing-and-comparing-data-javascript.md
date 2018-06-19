---
title: Копирование, передача и сравнение данных (JavaScript) | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], passing values
- function parameters
- string comparison
- function parameters, about function parameters
- ByRef argument
- arrays [Visual Studio], setting data types
- arrays [Visual Studio], copying data
- ByVal argument
- string comparison, testing data
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3cf980ca1dfd0c0e09871b6de9756cb2a10364b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569334"
---
# <a name="copying-passing-and-comparing-data-javascript"></a>Копирование, передача и сравнение данных (JavaScript)
В [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] то, как обрабатываются данные, зависит от типа данных.  
  
## <a name="by-value-vs-by-reference"></a>По значению и по ссылке  
 Числа и логические значения (**true** и **false**) копируются, передаются и сравниваются *по значению*. При копировании или передаче по значению в памяти компьютера выделяется место, в которое копируется значение исходного объекта. При изменении исходного числа или логической переменной копия не меняется (и наоборот), так как они представляют собой две разные сущности.  
  
 Объекты, массивы и функции копируются, передаются и сравниваются *по ссылке*. При копировании или передаче по ссылке фактически создается указатель на исходный элемент, а затем этот указатель используется как копия. Если изменить оригинал, будут изменены и оригинал, и копия (и наоборот). На самом деле существует только одна сущность; "копия" представляет собой просто ссылку на данные.  
  
 Для успешного сравнения по ссылке две переменные должны ссылаться на одну и ту же запись. Например, два отдельных объекта **Array** всегда будут не равны друг другу, даже если они содержат одинаковые элементы. Одна из переменных должна являться ссылкой на другую переменную, чтобы их сравнение было успешным. Чтобы проверить, совпадают ли элементы двух массивов, сравните результаты выполнения метода **toString()**.  
  
 Наконец, строки копируются и передаются по ссылке, но сравниваются по значению. Обратите внимание, что если имеется два объекта **String** (созданных оператором **new** String("что_нибудь")), они сравниваются по ссылке, но если одно или оба значения являются строковыми, они сравниваются по значению.  
  
> [!NOTE]
>  Наборы символов ASCII и ANSI созданы таким образом, что заглавные буквы стоят в порядке последовательности перед буквами нижнего регистра. Например, строка "Zoo" имеет *меньшее* значение по сравнению со строкой "aardvark". Чтобы выполнить сравнение без учета регистра, можно вызвать для обеих строк метод **toUpperCase()** или **toLowerCase()**.  
  
## <a name="passing-parameters-to-functions"></a>Передача параметров в функции  
 При передаче параметра в функцию по значению создается отдельная копия параметра, существующая только внутри этой функции. Хотя объекты и массивы передаются по ссылке, если непосредственно перезаписать их новых новым значением внутри функции, новое значение не будет применено за пределами этой функции. За пределами функции применяются только изменения свойств объектов или элементов массивов.  
  
 Пример (с использованием объектной модели Internet Explorer):  
  
```JavaScript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## <a name="testing-data"></a>Проверка данных  
 При проверке по значению два отдельных элемента сравниваются на предмет равенства. Обычно такое сравнение выполняется побитово. Проверка по ссылке позволяет узнать, являются ли два элемента указателями на один исходный элемент. Если это так, они считаются равными; если нет (даже если они содержат полностью, с точностью до байта, совпадающие значения), они считаются неравными.  
  
 Копирование и передача строк по ссылке экономит память; но так как невозможно изменить строки после создания, становится возможным сравнивать их по значению. Это позволяет проверить, совпадает ли содержимое двух строк, даже если одна из них была создана совершенно независимо от другой.  
  
## <a name="see-also"></a>См. также  
 [Вычисление даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)