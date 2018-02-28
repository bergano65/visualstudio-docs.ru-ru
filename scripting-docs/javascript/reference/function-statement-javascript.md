---
title: "функция оператор (JavaScript) | Документы Microsoft"
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>Оператор function (JavaScript)
Объявляет новую функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Параметры  
 `functionname`  
 Обязательный. Имя функции.  
  
 `arg1...argN`  
 Необязательно. Вспомогательный список аргументов, которые понимает данная функция, разделенных запятыми.  
  
 `statements`  
 Необязательно. Один или несколько[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] инструкции.  
  
## <a name="remarks"></a>Примечания  
 Использовать `function` инструкции для объявления функции для дальнейшего использования. Код, который содержится в `statements` не выполняется, пока функция вызывается из в другом месте в скрипте.  
  
 [Возвращают](../../javascript/reference/return-statement-javascript.md) оператор используется для возврата значения из функции. Необходимо использовать `return` оператора, программа будет возвращать при достижении конца функции. Если не `return` инструкция выполняется в функцию, или если `return` оператор не имеет выражения, функция возвращает значение `undefined`.  
  
> [!NOTE]
>  При вызове функции, не забудьте добавить круглые скобки и все обязательные аргументы. Вызов функции без скобок возвращает ссылку на функцию, а не результаты функции.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `function`.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Пример  
 Функции можно назначить переменной. Это показано в следующем примере:  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)