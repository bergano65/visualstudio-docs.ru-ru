---
title: Длине массива должно быть назначено конечное положительное число | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825508"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Длине массива должно быть назначено конечное положительное число
При задании **длина** свойства существующего **массива** объект, указанный длина массива, который не является положительным числом или нулем. Эта ошибка возникает при попытке присвоить значение для **длина** свойство `Array` объект, который является отрицательным или не является числом (`NaN`). Обратите внимание, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] автоматически преобразует дробные числа в целыми числами.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Положительное целое число, назначьте свойства length. Нет верхний предел для размера массива, превышающее максимальное целое число (примерно 4 миллиарда) отсутствует. В следующем примере показано, как правильно задать **длина** свойство **массива** объекта.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)