---
title: "Длине массива должно быть назначено конечное положительное число | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Длине массива должно быть назначено конечное положительное число
При задании **длина** свойства существующего **массива** объекта, указанного длина массива, который не является положительным числом или нулем. Эта ошибка возникает при попытке присвоить значение для **длина** свойство `Array` объекта, который является отрицательным или не является числом (`NaN`). Обратите внимание, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] автоматически преобразует дробных чисел в целые.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Положительное целое число, присваивается свойству length. Отсутствует верхний предел для размера массива, отличные от максимальное целое число (около 4 миллиардов). В следующем примере показано, как правильно установить **длина** свойство **массива** объекта.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)