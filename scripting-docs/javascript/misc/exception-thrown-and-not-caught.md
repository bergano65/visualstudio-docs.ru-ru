---
title: Исключение возникло, но не перехвачено | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946333"
---
# <a name="exception-thrown-and-not-caught"></a>Исключение возникло, но не перехвачено
Вы включены `throw` инструкции в коде, но не было заключены в **попробуйте** блока, или произошла сопоставленный **catch** блок для перехвата ошибок. Исключения изнутри **попробуйте** запретить, используя **throw** инструкции и перехватываются за пределами **попробуйте** блоке с **catch** инструкция.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Заключите код, который может создавать исключения в **попробуйте** блокировать и убедитесь, имеется соответствующий **catch** блока.  
  
- Убедитесь, что оператор catch ожидает правильной формой исключения.  
  
- Если исключение создается снова, убедитесь, что имеется другой соответствующий оператор catch.  
  
## <a name="see-also"></a>См. также  
 [Объект ошибки](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)