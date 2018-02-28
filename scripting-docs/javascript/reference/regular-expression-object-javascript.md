---
title: "Объект регулярного выражения (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Объект регулярного выражения (JavaScript)
Объект, который содержит шаблон регулярного выражения с флагами, определяющими, как применять шаблон.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Синтаксис  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Параметры  
 *RE*  
 Обязательный. Имя переменной, которой назначается шаблон регулярного выражения.  
  
 *шаблон*  
 Обязательный. Используемый шаблон регулярного выражения. Если вы используете синтаксис 1, разделите шаблон с помощью символов «/». Если вы используете синтаксис 2, заключите шаблон в кавычки.  
  
 `flags`  
 Необязательно. При использовании синтаксиса 2 заключите флаг в кавычки. Доступные флаги, которые можно совместить:  
  
-   g (глобальный поиск всех вхождений *шаблон*)  
  
-   i (не учитывать регистр);  
  
-   m (многостроковый поиск);  
  
-   u (Юникод), включает EcmaScript 6 [функции Юникода](../../javascript/advanced/special-characters-javascript.md). Поддерживается только в [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)];  
  
-   y (прикрепленное совпадение), ищет совпадения в свойстве `lastIndex` регулярного выражения (и не ищет в более поздних индексах). Поддерживается в [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Примечания  
 **Регулярное выражение** объекта не следует путать с глобальным `RegExp` объекта. Несмотря на их кажущееся сходство, они отличаются. Свойства **регулярное выражение** содержат только сведения об определенном **регулярное выражение** экземпляра, тогда как свойства глобального `RegExp` объект содержит постоянно обновляются сведения о каждом возникающем совпадении.  
  
 **Регулярное выражение** объекты хранят шаблоны, используемые при поиске сочетаний символов в строках. После **регулярное выражение** создается объект, он передается в строковый метод или строка, передаваемая в один из методов регулярных выражений. Сведения о последнем выполненном поиске хранятся в глобальном объекте `RegExp`.  
  
 Используйте синтаксис 1, если искомая строка заранее известна. Используйте синтаксис 2, если искомая строка часто меняется или неизвестна (примером может служить строка, взятая из входных данных от пользователя).  
  
 *Шаблон* аргумент компилируется во внутренний формат перед использованием. В синтаксисе 1 *шаблон* компилируется в ходе загрузки скрипта. Для синтаксиса 2 *шаблон* компилируется непосредственно перед использованием или при **компиляции** вызывается метод.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **регулярное выражение** объекта путем создания объекта (re), содержащего шаблон регулярного выражения со связанными флагами. В этом случае полученный **регулярное выражение** объект затем используется `match` метод:  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>Пример  
 В следующем примере обновляется шаблон регулярного выражения: разрешается поиск нескольких экземпляров.  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>Пример  
 Если используется флаг /y, при нахождении совпадения он обновляет `lastindex` до индекса следующего символа после последнего совпадения. При ненахождении совпадения он сбрасывает `lastindex` до 0.  
  
 В следующем примере выполняется поиск совпадения в определенном индексе с использованием флага /y и свойства `lastIndex`.  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>Свойства  
 [глобальное свойство](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [свойство ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [свойство multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [свойство source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Методы  
 [Метод Compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [метод exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [метода теста](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Флаг u поддерживается в [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 Флаг y поддерживается в [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Объект String](../../javascript/reference/string-object-javascript.md)