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
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862766"
---
# <a name="exception-thrown-and-not-caught"></a>Исключение возникло, но не перехвачено
Вы включили `throw` в код оператор, но он не был заключен в блок **try** , или нет связанного блока **catch** для перехвата ошибки. Исключения создаются в блоке **try** с помощью инструкции **throw** и перехватываются вне блока **try** с помощью оператора **catch** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Заключите код, который может вызвать исключение в блоке **try** , и убедитесь, что имеется соответствующий блок **catch** .  
  
- Убедитесь, что оператор catch имеет правильную форму исключения.  
  
- Если исключение создается повторно, убедитесь, что имеется другой соответствующий оператор catch.  
  
## <a name="see-also"></a>См. также  
 [Объект Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Оператор Throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [Попробуйте... перехватить... Оператор finally](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)