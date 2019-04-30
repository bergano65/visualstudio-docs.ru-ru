---
title: Длине массива должно быть назначено конечное положительное число | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39f2720efbcd8defffb9d0c77047a50e57939e95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818056"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Длина массива должна быть указана в виде конечного положительного числа
При задании **длина** свойства существующего **массива** объект, указанный длина массива, который не является положительным числом или нулем. Эта ошибка возникает при попытке присвоить значение для **длина** свойство `Array` объект, который является отрицательным или не является числом (`NaN`). Обратите внимание, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] автоматически преобразует дробные числа в целыми числами.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Положительное целое число, назначьте свойства length. Нет верхний предел для размера массива, превышающее максимальное целое число (примерно 4 миллиарда) отсутствует. В следующем примере показано, как правильно задать **длина** свойство **массива** объекта.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)