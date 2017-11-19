---
title: "Ожидалась строка | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2dabf754b2bfb4b20555b41457df04d54a5c31c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="string-expected"></a>Ожидалась строка
Предпринята попытка вызвать **String.prototype.toString** или **String.prototype.valueOf** метода объекта типа, отличного от `String`. Объект вызова этого типа должен иметь тип `String`.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывать только **String.prototype.toString** или **String.prototype.valueOf** методов для объектов типа `String`.  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Метод toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)