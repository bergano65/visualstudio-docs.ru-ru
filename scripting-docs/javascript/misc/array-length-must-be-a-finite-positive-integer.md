---
title: Длина массива должна быть конечным положительным числом | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348598"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Длина массива должна быть конечным положительным числом
При вызове **массива** конструктор с аргументом, который не является целым числом (целые числа состоят из нуля, а также набор положительные целые числа).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Использовать положительные целые числа, только в том случае, при создании нового `Array` объекта. Если вы хотите создать массив с единственным элементом, который не является целым числом, сделайте это в два этапа. Сначала создайте массив с одним элементом, а затем поместить значение в первом элементе (array[0]). Ниже приведен пример, который создает эту ошибку.  
  
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