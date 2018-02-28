---
title: "Оператор Do... while (JavaScript) | Документы Microsoft"
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
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>Оператор do...while (JavaScript)
Один раз выполняет блок операторов, а затем повторяет выполнение цикла, пока условное выражение, результатом которого является `false`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Параметры  
 `statement`  
 Обязательный. Инструкции для выполнения, если `expression` — `true`. Может быть составным оператором.  
  
 `expression`  
 Обязательный. Выражение, которое может быть преобразовано в логическое значение `true` или `false`. Если `expression` — `true`, повторного выполнения цикла. Если `expression` — `false`, выполнение цикла прекращается.  
  
## <a name="remarks"></a>Примечания  
 В отличие от `while` инструкции `do...while` цикл выполняется один раз, прежде чем условное выражение.  
  
 В любой строке `do...while` блока, можно использовать `break` можно использовать инструкцию, чтобы вызвать программного потока для выхода из цикла, или `continue` инструкцию, чтобы перейти непосредственно на `while` выражение.  
  
## <a name="example"></a>Пример  
 В следующем примере инструкции в `do...while` продолжать выполнение, пока переменная цикла `i` меньше 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Пример  
 В следующем примере операторы внутри цикла выполняются один раз, несмотря на то, что условие не выполнено.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор Continue](../../javascript/reference/continue-statement-javascript.md)   
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [for... в инструкции](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор While](../../javascript/reference/while-statement-javascript.md)   
 [Оператор с меткой](../../javascript/reference/labeled-statement-javascript.md)