---
title: Ожидался объект регулярного выражения | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370e5a8028bae0e60c265ba65dca12668e4b8d8c
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862065"
---
# <a name="regular-expression-object-expected"></a>Предполагается наличие объекта регулярного выражения
Предпринята попытка вызвать метод **RegExp. prototype. ToString** или **RegExp. prototype. valueOf** для объекта типа, отличного от `RegExp` . Объект этого типа вызова должен иметь тип `RegExp` .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **RegExp. prototype. ToString** или **RegExp. prototype. valueOf** для объектов типа `RegExp` .  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Синтаксис регулярных выражений (JavaScript)](/previous-versions/1400241x(v=vs.100))