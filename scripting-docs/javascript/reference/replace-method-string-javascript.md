---
title: "Метод replace (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="replace-method-string-javascript"></a>Метод replace (String) (JavaScript)
Заменяет текст в строке, используя регулярное выражение или строку поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательно. Объект `String` или строковый литерал, в котором выполняется замена. Эта строка не изменяется методом **заменить** метод. Вместо этого метод возвращает строку, созданную заменой.  
  
 `rgExp`  
 Обязательно. Экземпляр **регулярное выражение** объект, содержащий шаблон регулярного выражения и установленные флаги. Также может быть объектом `String` или строковым литералом, представляющим регулярное выражение. Если `rgExp` не является экземпляром **регулярное выражение** объекта, он преобразуется в строку и выполняется поиск точного соответствия выполняется для результатов, не предпринимается попытка преобразовать строку в регулярном выражении.  
  
 `replaceText`  
 Обязательно. Объект `String` или строковый литерал, содержащий текст, на который требуется заменить все найденные соответствия аргумента `rgExp` в объекте `stringObj`. В [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] и более поздних версиях аргумент `replaceText` может быть также функцией, возвращающей текст замены.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Результат **заменить** метод представляет собой копию `stringObj` после внесения указанных замен.  
  
## <a name="remarks"></a>Примечания  
 Ниже указаны переменные соответствия, которые можно использовать для определения последнего найденного соответствия и содержащей его строки. Переменные соответствия можно использовать при замене текста, если строка для замены должна определяться динамически.  
  
|Знаки|Значение|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
|**$&**|Определяет часть `stringObj`, с которой совпадает весь шаблон. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
|`$``|Определяет часть `stringObj` , предшествующую совпадению, описываемого  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
|`$'`|Определяет часть `stringObj` , следующую за совпадением, описываемого  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
|`$`  ***n***| *n* Th частичное совпадение под, где  *n*  является одна десятичная цифра от 1 до 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
|`$`  ***nn***| *nn* Th частичное совпадение под, где  *nn*  — это 2 разряда десятичное число от 01 до 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии)|  
  
 Если `replaceText` является функцией, то для каждой найденной подстроки функция вызывается следующим *m* + 3 аргумента где *m* число открывающих круглых скобок в `rgExp`. Первым аргументом является подстрока, поиск которой выполняется. Следующий *m* аргументов — это все совпадения, обнаруженные во время поиска. Аргумент *m* + 2 — это смещение в `stringObj` где нашлось совпадение, а аргумент *m* + 3 — `stringObj`. Результатом является строка, в которой все найденные подстроки заменены соответствующим значением, возвращаемым вызываемой функцией.  
  
 **Заменить** метод обновляет свойства глобального `RegExp` объекта.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **заменить** метод для замены всех вхождений «» на «».  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Кроме того **заменить** позволяет заменять подвыражения в шаблоне. В следующем примере меняются местами все пары слов в строке.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 В следующем примере, который работает в [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] и более поздних версиях, показано, как использовать функцию, возвращающую текст замены. Она заменяет любой экземпляр числа перед "F" с преобразованием в градусы Цельсия.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Метод Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Метод Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод Test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Программирование регулярных выражений (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Чередование и части выражений (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Обратные ссылки (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 перетаскивание примера приложения](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)