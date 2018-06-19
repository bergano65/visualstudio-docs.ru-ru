---
title: Оператор for (JavaScript) | Документы Microsoft
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
- for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637144"
---
# <a name="for-statement-javascript"></a>Оператор for (JavaScript)
Выполняет блок операторов, пока указанное условие истинно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Параметры  
 `initialization`  
 Необязательно. Выражения. Данное выражение выполняется только один раз, перед выполнением цикла.  
  
 `test`  
 Необязательно. Выражение типа Boolean. Если `test` — `true`, `statement` выполняется. Если `test` Если `false`, выполнение цикла прекращается.  
  
 `increment`  
 Необязательно. Выражения. Выражение увеличения выполняется в конце каждого прохода цикла.  
  
 `statement`  
 Необязательно. Один или несколько операторов для выполнения, если `test` — **true**. Может быть составным оператором.  
  
## <a name="remarks"></a>Примечания  
 Обычно используется `for` цикл, когда цикл необходимо выполнить известное количество раз. Объект `for` цикл удобно использовать для перебора массивов и для последовательной обработки.  
  
 Тест условного выражения осуществляется до выполнения цикла, поэтому `for` инструкция выполняет ноль или более раз.  
  
 В любой строке `for` блока инструкций цикла, можно использовать `break` можно использовать инструкцию, чтобы выйти из цикла, или `continue` передать управление в следующую итерацию цикла.  
  
## <a name="example"></a>Пример  
 В следующем примере `for` инструкция выполняет заключенные в цикл инструкции следующим образом:  
  
-   Во-первых, начальное значение переменной `i` вычисляется.  
  
-   Затем, при условии, что значение `i` меньше или равно 9, `document.write` инструкции и `i` перестраивается.  
  
-   Когда `i` больше 9, условие становится ложным и управление передается за пределы цикла.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Пример  
 Все выражения из `for` инструкции являются необязательными. В следующем примере `for` инструкции создают бесконечный цикл и `break` оператор используется для выхода из цикла.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [for... в инструкции](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)