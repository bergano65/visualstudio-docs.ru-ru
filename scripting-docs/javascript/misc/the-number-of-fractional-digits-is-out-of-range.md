---
title: Число цифр дробной части выходит за пределы допустимого диапазона | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 1b0eb1d7a53614f48daaf6459aaadee594b6fa11
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816180"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Число цифр дробной части не соответствует допустимому диапазону
Предпринята попытка передать недопустимый аргумент в функцию **Number. prototype. toExponential**. Аргумент функции **toExponential ()** должен находиться в диапазоне от 0 до 20 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что аргумент для **toExponential ()** не слишком велик или не слишком мал.  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)