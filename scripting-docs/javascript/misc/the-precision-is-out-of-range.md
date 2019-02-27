---
title: Точность выходит за пределы диапазона | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 875f09acb6a9ab66c656524a7bb2a1a61cbcdb6f
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839806"
---
# <a name="the-precision-is-out-of-range"></a>Точность не соответствует допустимому диапазону
Была предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toPrecision**. Аргумент **toPrecision** должен быть от 1 до 21 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Аргумент для `toPrecision` не слишком велико или слишком мало.  
  
## <a name="see-also"></a>См. также  
 [Метод toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)