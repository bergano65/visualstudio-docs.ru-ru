---
title: "Оператор Continue (JavaScript) | Документы Microsoft"
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
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="continue-statement-javascript"></a>Оператор continue (JavaScript)
Останавливает текущую итерацию цикла и запускает новую итерацию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный `label` аргумент указывает инструкцию, к которому `continue` применяется.  
  
 Можно использовать `continue` инструкции только внутри `while`, `do...while`, **для**, или `for...in` цикла. Выполнение `continue` инструкция Останавливает текущую итерацию цикла и программы продолжается с начала цикла. Это оказывает следующее влияние на различные типы циклов:  
  
-   `while`и `do...while` циклы их условие теста и значение true, если цикла повторного выполнения.  
  
-   `for`циклы выполняют выражение увеличения и, если выражение имеет значение true, выполните цикл снова.  
  
-   `for...in`циклы перейти к следующему полю указанной переменной и повторного выполнения цикла.  
  
## <a name="examples"></a>Примеры  
 В этом примере цикл последовательно от 1 до 9. Инструкции между `continue` и концом `for` body пропускаются из-за использования `continue` инструкции вместе с выражением `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 В следующем коде `continue` Инструкция ссылается на `for` цикл, который предшествует `Inner:` метки. Когда `j` 24, `continue` инструкция вызывает, `for` переход к следующей итерации цикла. Значения от 21 до 23 и 25 до 30 печати в каждой строке.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [for... в инструкции](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор с меткой](../../javascript/reference/labeled-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)