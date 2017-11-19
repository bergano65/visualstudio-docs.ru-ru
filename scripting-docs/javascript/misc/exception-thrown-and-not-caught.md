---
title: "Исключение возникло, но не перехвачено | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Исключение возникло, но не перехвачено
Вы включены `throw` инструкции в коде, но он не был включен в **повторите** блока, возникла не связан или **перехватывать** блок для перехвата ошибок. Исключения из среды **повторите** с помощью **throw** инструкции и перехватываются за пределами **повторите** блоке с **перехватывать** инструкция.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Заключите код, который может вызывать исключение в **повторите** блокировку и обеспечить имеется соответствующий **перехватывать** блока.  
  
-   Убедитесь, что оператор catch ожидает исключение правильной формы.  
  
-   Если исключение создается повторно, убедитесь, что имеется другой соответствующий оператор catch.  
  
## <a name="see-also"></a>См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)