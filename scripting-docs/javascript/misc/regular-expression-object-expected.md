---
title: Ожидался объект регулярного выражения | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 2b27c90a0c2461d500f618fbf7acede4d6942781
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840677"
---
# <a name="regular-expression-object-expected"></a>Предполагается наличие объекта регулярного выражения
Предпринята попытка вызова **RegExp.prototype.toString** или **RegExp.prototype.valueOf** метод на объект типа, отличных от `RegExp`. Объект этого типа вызова должен иметь тип `RegExp`.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывается только **RegExp.prototype.toString** или **RegExp.prototype.valueOf** методов в объектах типа `RegExp`.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)