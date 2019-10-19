---
title: Точность вне допустимого диапазона | Документация Майкрософт
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
ms.openlocfilehash: 364794472cbf17643cebbd926cd3fda6e93be1f9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577282"
---
# <a name="the-precision-is-out-of-range"></a>Точность не соответствует допустимому диапазону
Предпринята попытка передать недопустимый аргумент в функцию **Number. prototype. toPrecision**. Аргумент для **toPrecision** должен находиться в диапазоне от 1 до 21 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что аргумент для `toPrecision` не слишком велик или слишком мал.  
  
## <a name="see-also"></a>См. также  
 [Метод toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)