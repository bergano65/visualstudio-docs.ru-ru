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
ms.openlocfilehash: d9f5816c0bf3ad7c8dbf7d394952c631923d89cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814633"
---
# <a name="regular-expression-object-expected"></a>Предполагается наличие объекта регулярного выражения
Предпринята попытка вызвать метод **RegExp. prototype. ToString** или **RegExp. prototype. valueOf** для объекта типа, отличного от `RegExp` . Объект этого типа вызова должен иметь тип `RegExp` .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **RegExp. prototype. ToString** или **RegExp. prototype. valueOf** для объектов типа `RegExp` .  
  
## <a name="see-also"></a>См. также раздел  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)