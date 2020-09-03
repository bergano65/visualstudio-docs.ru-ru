---
title: Исключение вызвано и не перехвачено | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814594"
---
# <a name="exception-thrown-and-not-caught"></a>Исключение возникло, но не перехвачено
Вы включили `throw` в код оператор, но он не был заключен в блок **try** , или нет связанного блока **catch** для перехвата ошибки. Исключения создаются в блоке **try** с помощью инструкции **throw** и перехватываются вне блока **try** с помощью оператора **catch** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Заключите код, который может вызвать исключение в блоке **try** , и убедитесь, что имеется соответствующий блок **catch** .  
  
- Убедитесь, что оператор catch имеет правильную форму исключения.  
  
- Если исключение создается повторно, убедитесь, что имеется другой соответствующий оператор catch.  
  
## <a name="see-also"></a>См. также раздел  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [Оператор Throw](../../javascript/reference/throw-statement-javascript.md)   
 [Попробуйте... перехватить... Оператор finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)