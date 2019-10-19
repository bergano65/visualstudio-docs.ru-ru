---
title: Длина массива должна быть конечным положительным целым числом | Документация Майкрософт
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
ms.openlocfilehash: 69494f1485a97ff4f2c98cf2493e5d0bc5b8aa9f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576076"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Длина массива должна быть выражена конечным положительным числом
При вызове конструктора **массива** с аргументом, который не является целым числом (целые числа состоят из нуля и набора положительных целых чисел).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Используйте положительные целые числа только при создании нового объекта `Array`. Если нужно создать массив с одним элементом, который не является целым числом, сделайте это в два этапа. Сначала создайте массив с одним элементом, а затем поместите значение в первый элемент (массив [0]). Ниже приведен пример, в котором создается эта ошибка.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     В следующем примере показан правильный способ указания массива с одним числовым элементом.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Отсутствует верхний предел размера массива, кроме максимального целого значения (приблизительно 4 000 000 000).  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)