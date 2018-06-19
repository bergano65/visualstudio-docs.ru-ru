---
title: Оператор Return (JavaScript) | Документы Microsoft
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
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639334"
---
# <a name="return-statement-javascript"></a>Оператор return (JavaScript)
Завершает выполнение текущей функции и возвращает ее значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный *выражение* аргумент имеет значение возвращается из функции. Если не указано, функция возвращает значение.  
  
 Вы используете `return` инструкцию, чтобы остановить выполнение функции и возврата значения *выражение*. Если *выражение* опущен, или не `return` инструкция выполняется в функции, выражение, вызывавшие текущую функцию присваивается значение undefined.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `return`.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `return` для возврата функции.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)