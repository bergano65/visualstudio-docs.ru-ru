---
title: 0... n свойства (аргументы) (JavaScript) | Документы Microsoft
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
- 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634014"
---
# <a name="0n-properties-arguments-javascript"></a>Свойства 0...n (arguments) (JavaScript)
Возвращает фактическое значение отдельные аргументы из **аргументы** объект, возвращаемый **аргументы** свойство выполняемой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Параметры  
 *function*  
 Необязательно. Имя выполняемого в настоящее время `Function` объекта.  
  
 0, 1, 2, *, n*  
 Обязательный. Неотрицательное целое число в диапазоне от 0 до  *n*  где 0 представляет первый аргумент и  *n*  представляет последний аргумент. Значение последним аргументом  *n*  — **arguments.length-1**.  
  
## <a name="remarks"></a>Примечания  
 Значения, возвращаемые в 0. . . фактические значения, переданные функции, выполняемой в n свойства: При фактически не массив аргументов, отдельные аргументы, составляющие **аргументы** объекта осуществляется так же, что элементы массива будут доступны.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **0...**  ***n***свойства **аргументы** объекта. Чтобы полностью понять в примере, передайте один или несколько аргументов функции:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Функции объекта](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Length (аргументы)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Свойство length (функция)](../../javascript/reference/length-property-function-javascript.md)