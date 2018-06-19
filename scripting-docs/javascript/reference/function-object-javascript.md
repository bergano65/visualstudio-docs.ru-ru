---
title: Функция объект (JavaScript) | Документы Microsoft
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637374"
---
# <a name="function-object-javascript"></a>Объект Function (JavaScript)
Создает новую функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Параметры  
 `functionName`  
 Обязательный. Имя созданного функции  
  
 `argname1...argnameN`  
 Необязательно. Список аргументов, который принимает функция.  
  
 `body`  
 Необязательно. Строка, содержащая блок [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] код, выполняемый при вызове функции.  
  
## <a name="remarks"></a>Примечания  
 Функция является типом данных в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Синтаксис 1 создает значение функции [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] преобразует в `Function` объекта при необходимости. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Преобразует `Function` объекты, создаваемые синтаксиса 2 в значения функции во время вызова функции.  
  
 Синтаксис 1 — стандартный способ создания новых функций в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Используется для создания объектов функций явно альтернативную форму используется синтаксис 2.  
  
 Например чтобы объявить функцию, которая добавляет два аргумента, переданного ему, это можно сделать одним из двух способов:  
  
## <a name="example-1"></a>Пример 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Пример 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 В любом случае вызове функции со строкой кода следующего вида:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  При вызове функции, убедитесь, что всегда включать круглые скобки и все обязательные аргументы. Вызов функции без скобок вызывает функция должны быть возвращены вместо возвращаемого значения функции.  
  
## <a name="properties"></a>Свойства  
 [0... n свойства](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ Свойство arguments](../../javascript/reference/arguments-property-function-javascript.md) &#124; [свойство callee](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [свойство caller](../../javascript/reference/caller-property-function-javascript.md) &#124; [свойство constructor](../../javascript/reference/constructor-property-object-javascript.md) &#124; [свойство length (функция)](../../javascript/reference/length-property-function-javascript.md) &#124; [свойство prototype](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Методы  
 [Метод Apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [метод bind](../../javascript/reference/bind-method-function-javascript.md) &#124; [вызовите метод](../../javascript/reference/call-method-function-javascript.md) &#124; [метод toString](../../javascript/reference/tostring-method-object-javascript.md) &#124; [метод valueOf](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор Function](../../javascript/reference/function-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Оператор var](../../javascript/reference/var-statement-javascript.md)