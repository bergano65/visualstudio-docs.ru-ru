---
title: Число цифр дробной части выходит за пределы диапазона | Документы Microsoft
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
- VS.WebClient.Help.SCRIPT5026
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17ffec5e6b4cfff85b49f61e7105ca8ce3d75c78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633184"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Число цифр дробной части вне диапазона
Предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toExponential**. Аргумент функции **toExponential()** должен находиться в диапазоне от 0 до 20 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Аргумент для обеспечения **toExponential()** не слишком велик или слишком мал.  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)