---
title: Число цифр дробной части выходит за пределы диапазона | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5026
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78b8d3773731a1135bff75a3c2d3b35696f065b8
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842949"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Число цифр дробной части не соответствует допустимому диапазону
Была предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toExponential**. Аргумент функции **toExponential()** должен находиться в диапазоне от 0 до 20 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Аргумент для **toExponential()** не слишком велико или слишком мало.  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)