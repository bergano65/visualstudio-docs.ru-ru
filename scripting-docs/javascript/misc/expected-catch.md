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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841459"
---
# <a name="expected-catch"></a>Ожидалось ключевое слово "catch"
Вы использовали обработки исключений **попробуйте** block, но не писали связанного **catch** инструкции. Требуется механизм обработки исключений, что код, который может завершиться ошибкой, а также код, который не должен выполняться при возникновении исключения, заключаться в **попробуйте** блока. Исключения изнутри **попробуйте** запретить, используя **throw** инструкции и перехватываются за пределами **попробуйте** блок с одним или несколькими **catch**инструкций.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавление связанного **catch** блока.  
  
-   Попробуйте использовать **наконец** блокировать вместо **catch** блока.  
  
## <a name="see-also"></a>См. также  
 [Try... catch... finally инструкции](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)