---
title: Оператору throw должно следовать выражение в той же строке исходного кода | Документация Майкрософт
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572759"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>throw требует после себя выражение на той же строке
Использовалось ключевое слово `throw`, но оно не следовало бы за выражением в той же исходной строке. Оператор `throw` состоит из двух частей: ключевого слова `throw`, за которым следует вызываемое выражение. Например:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Эти два компонента не могут быть разделены.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что в одной строке отображаются ключевое слово `throw` и выражение, которое должно быть создано.  
  
## <a name="see-also"></a>См. также:  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)