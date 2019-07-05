---
title: Требуется строка | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6853d92608859e41fd7d8001ca6e350f5830504
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006461"
---
# <a name="string-expected"></a>Требуется строка
Предпринята попытка вызова **String.prototype.toString** или **String.prototype.valueOf** метод на объект типа, отличных от `String`. Объект этого типа вызова должен иметь тип `String`.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызывается только **String.prototype.toString** или **String.prototype.valueOf** методов в объектах типа `String`.  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Метод toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)