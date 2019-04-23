---
title: Ожидалось ключевое слово «catch» | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053236"
---
# <a name="expected-catch"></a>Ожидалось ключевое слово "catch"
Вы использовали обработки исключений **попробуйте** block, но не писали связанного **catch** инструкции. Требуется механизм обработки исключений, что код, который может завершиться ошибкой, а также код, который не должен выполняться при возникновении исключения, заключаться в **попробуйте** блока. Исключения изнутри **попробуйте** запретить, используя **throw** инструкции и перехватываются за пределами **попробуйте** блок с одним или несколькими **catch**инструкций.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавление связанного **catch** блока.  
  
- Попробуйте использовать **наконец** блокировать вместо **catch** блока.  
  
## <a name="see-also"></a>См. также  
 [Try... catch... finally инструкции](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)