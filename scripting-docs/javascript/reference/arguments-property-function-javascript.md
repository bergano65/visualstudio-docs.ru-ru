---
title: "Свойство arguments (Function) (JavaScript) | Документы Microsoft"
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>Свойство arguments (Function) (JavaScript)
Возвращает аргументы для выполняющегося в данный момент `Function` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Примечания  
 `function` Аргумента — имя текущей выполняемой функции и может быть опущено.  
  
 Это свойство предоставляет функцию для обработки переменное число аргументов. **Длина** свойство `arguments` объект содержит количество аргументов, переданных в функцию. Отдельные аргументы, содержащиеся в `arguments` объекту осуществляется таким же образом, элементы массива.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение свойства `arguments`.  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Оператор function](../../javascript/reference/function-statement-javascript.md)