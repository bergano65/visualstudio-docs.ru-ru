---
title: Требуется "Catch" | Документация Майкрософт
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573424"
---
# <a name="expected-catch"></a>Ожидалось ключевое слово "catch"
Вы использовали блок **try** обработки исключений, но не написали соответствующий оператор **catch** . Механизм обработки исключений требует, чтобы код, который может завершиться ошибкой, вместе с кодом, который не должен выполняться при возникновении исключения, был заключен внутрь блока **try** . Исключения создаются в блоке **try** с помощью инструкции **throw** и перехватываются вне блока **try** с помощью одного или нескольких инструкций **catch** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте связанный блок **catch** .  
  
- Попробуйте использовать блок **finally** вместо блока **catch** .  
  
## <a name="see-also"></a>См. также:  
 [попробуйте... перехватить... Оператор finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)