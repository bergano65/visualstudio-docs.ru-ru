---
title: Число цифр дробной части выходит за пределы допустимого диапазона | Документация Майкрософт
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
ms.openlocfilehash: 8697e31e021fd0042046a46d2ac1f0c8a441b402
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572769"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Число цифр дробной части не соответствует допустимому диапазону
Предпринята попытка передать недопустимый аргумент в функцию **Number. prototype. toExponential**. Аргумент функции **toExponential ()** должен находиться в диапазоне от 0 до 20 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что аргумент для **toExponential ()** не слишком велик или не слишком мал.  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)