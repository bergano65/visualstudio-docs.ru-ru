---
title: "Длина массива должна быть конечным положительным числом | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Длина массива должна быть конечным положительным числом
Вы вызываете **массива** конструктор с аргументом, который не является целым числом (целые числа состоят из нуля, а также набор положительные целые числа).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Использовать положительные целые числа, только при создании нового `Array` объекта. Если вы хотите создать массив с единственным элементом, который не является целым числом, это можно сделать в два этапа. Сначала создайте массив с одним элементом, а затем поместить значение в первом элементе (array[0]). Ниже приведен пример, который создает эту ошибку.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Ниже приведен пример правильный способ задания массива с одним числовым элементом.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Отсутствует верхний предел для размера массива, отличные от максимальное целое число (около 4 миллиардов).  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)