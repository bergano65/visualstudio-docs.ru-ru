---
title: "Объект arguments (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>Объект arguments (JavaScript)
Объект, представляющий аргументы текущей выполняемой функции и функциям, обратившимся к объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Параметры  
 *function*  
 Необязательно. Имя выполняемого в настоящее время `Function` объекта.  
  
 *n*  
 Обязательный. Отсчитываемый от нуля индекс значения аргумент, передаваемый `Function` объекта.  
  
## <a name="remarks"></a>Примечания  
 Невозможно явно создать **аргументы** объекта. **Аргументы** объект доступен, только когда начинается выполнение функции. **Аргументы** объект функции, не является массивом, но доступа к элементам массива осуществляется так же, как отдельные аргументы. Индекс  *n*  является ссылкой на один из **0**  ***n***  свойства **аргументы** объекта.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **аргументы** объекта.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [0... n свойства (аргументы)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Свойство callee (arguments)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Свойство length (аргументы)](../../javascript/reference/length-property-arguments-javascript.md)