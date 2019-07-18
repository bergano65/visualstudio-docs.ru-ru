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
ms.openlocfilehash: 92a6e7fc6433f120c053303421feb5e8d58bd1c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006199"
---
# <a name="the-precision-is-out-of-range"></a>Точность не соответствует допустимому диапазону
Была предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toPrecision**. Аргумент **toPrecision** должен быть от 1 до 21 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Аргумент для `toPrecision` не слишком велико или слишком мало.  
  
## <a name="see-also"></a>См. также  
 [Метод toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)