---
title: "Ожидается &#39; catch &#39; | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>Ожидается &#39; catch &#39;
Использовать обработку исключений **повторите** блокировки, но не были записаны связанного **перехватывать** инструкции. Механизм обработки исключений требует, что код, который может завершиться ошибкой, а также код, который не следует выполнять при возникновении исключения быть упакован в **повторите** блока. Исключения из среды **повторите** с помощью **throw** инструкции и перехватываются за пределами **повторите** блок с одним или несколькими **перехватывать**инструкции.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавление связанного **перехватывать** блока.  
  
-   Попробуйте использовать **наконец** блокировать вместо **перехватывать** блока.  
  
## <a name="see-also"></a>См. также  
 [Try... catch... finally инструкции](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)