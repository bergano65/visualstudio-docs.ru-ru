---
title: Throw может стоять выражение на той же строке кода | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8ed951fb30b84f114f8f44a60e94b88f0f1d0f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069527"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw требует после себя выражение на той же строке
Вы использовали `throw` ключевое слово, но не соответствует его с помощью выражения в той же строке кода. Объект `throw` оператор состоит из двух частей: `throw` ключевое слово, и выражение исключение. Пример:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Вам не удается разделить эти два компонента.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что `throw` ключевое слово и выражение исключение появляется в той же строке.  
  
## <a name="see-also"></a>См. также  
 [Объект ошибки](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)