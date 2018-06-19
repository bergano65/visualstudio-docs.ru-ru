---
title: Оператор break (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634154"
---
# <a name="break-statement-javascript"></a>Оператор break (JavaScript)
Завершает текущий цикл или, если в сочетании с `label`, завершает связанный с ним оператор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный `label` аргумент задает метку инструкции прекращается.  
  
 Как правило, используется `break` инструкции в `switch` инструкций и в `while`, `for`, `for...in`, или `do...while` циклы. Чаще всего используется `label` аргумент в `switch` операторы, но его можно использовать в любой инструкции простых и составных.  
  
 Выполнение `break` инструкция выполняет выход из текущего цикла или оператора и начинается с оператора, следующего выполнения скрипта.  
  
## <a name="examples"></a>Примеры  
 В этом примере набор счетчиков для подсчета от 1 до 99; Однако `break` инструкция завершает цикл после 14 счетчиков.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 В следующем коде `break` Инструкция ссылается на `for` цикл, который предшествует `Inner:` инструкции. Когда `j` равняется 24, `break` инструкция вызывает программного потока для выхода из цикла. Значения от 21 до 23 печати в каждой строке.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор Continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [for... в инструкции](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор с меткой](../../javascript/reference/labeled-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)