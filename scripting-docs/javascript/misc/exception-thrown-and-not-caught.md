---
title: Исключение вызвано и не перехвачено | Документация Майкрософт
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572854"
---
# <a name="exception-thrown-and-not-caught"></a>Исключение возникло, но не перехвачено
Вы включили в код оператор `throw`, но он не был заключен в блок **try** или отсутствует связанный блок **catch** для перехвата ошибки. Исключения создаются в блоке **try** с помощью инструкции **throw** и перехватываются вне блока **try** с помощью оператора **catch** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Заключите код, который может вызвать исключение в блоке **try** , и убедитесь, что имеется соответствующий блок **catch** .  
  
- Убедитесь, что оператор catch имеет правильную форму исключения.  
  
- Если исключение создается повторно, убедитесь, что имеется другой соответствующий оператор catch.  
  
## <a name="see-also"></a>См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)    
 [оператор throw](../../javascript/reference/throw-statement-javascript.md)    
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)