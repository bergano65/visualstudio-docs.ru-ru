---
title: Незавершенный комментарий | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814807"
---
# <a name="unterminated-comment"></a>Комментарий без признака завершения
Вы начали многострочный комментарий, но не завершили его правильно. Многострочные комментарии начинаются с сочетания "/*" и заканчиваются на обратную \* комбинацию "/". Ниже представлен пример такого кода:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Не забудьте прервать многострочные комментарии с помощью "*/".  
  
## <a name="see-also"></a>См. также раздел  
 [Операторы комментария](../../javascript/reference/comment-statements-javascript.md)