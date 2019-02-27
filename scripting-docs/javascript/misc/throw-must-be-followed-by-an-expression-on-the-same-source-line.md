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
ms.openlocfilehash: 5d2989b2ebb5cf0095736d5667f85a807558c495
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841147"
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
  
-   Убедитесь, что `throw` ключевое слово и выражение исключение появляется в той же строке.  
  
## <a name="see-also"></a>См. также  
 [Объект ошибки](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)