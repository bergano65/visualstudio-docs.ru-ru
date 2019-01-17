---
title: Число цифр дробной части выходит за пределы диапазона | Документация Майкрософт
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
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348468"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>Число цифр дробной части вне диапазона
Была предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toExponential**. Аргумент функции **toExponential()** должен находиться в диапазоне от 0 до 20 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Аргумент для **toExponential()** не слишком велико или слишком мало.  
  
## <a name="see-also"></a>См. также  
 [Метод toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)