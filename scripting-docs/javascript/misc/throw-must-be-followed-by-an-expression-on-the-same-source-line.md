---
title: Оператору throw должно следовать выражение в той же строке исходного кода | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815530"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw требует после себя выражение на той же строке
Вы использовали `throw` ключевое слово, но не выполнили выражение в той же строке исходного кода. `throw`Оператор состоит из двух частей: `throw` ключевого слова, за которым следует вызываемое выражение. Пример:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Эти два компонента не могут быть разделены.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что `throw` ключевое слово и выражение, которые должны быть созданы, отображаются в одной строке.  
  
## <a name="see-also"></a>См. также раздел  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [Оператор Throw](../../javascript/reference/throw-statement-javascript.md)   
 [Попробуйте... перехватить... Оператор finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)