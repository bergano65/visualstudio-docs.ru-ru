---
title: Длина массива должна быть конечным положительным числом | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31673205a7ca94783985e0249c5664b4bbca6147
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073986"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Длина массива должна быть выражена конечным положительным числом
При вызове **массива** конструктор с аргументом, который не является целым числом (целые числа состоят из нуля, а также набор положительные целые числа).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Использовать положительные целые числа, только в том случае, при создании нового `Array` объекта. Если вы хотите создать массив с единственным элементом, который не является целым числом, сделайте это в два этапа. Сначала создайте массив с одним элементом, а затем поместить значение в первом элементе (array[0]). Ниже приведен пример, который создает эту ошибку.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Следующий пример демонстрирует правильный способ указания массива с помощью одного числового элемента.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Нет верхний предел для размера массива, превышающее максимальное целое число (примерно 4 миллиарда) отсутствует.  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)