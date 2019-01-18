---
title: Ожидалось ключевое слово «catch» | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344113"
---
# <a name="expected-catch"></a>Ожидалось ключевое слово "catch"
Вы использовали обработки исключений **попробуйте** block, но не писали связанного **catch** инструкции. Требуется механизм обработки исключений, что код, который может завершиться ошибкой, а также код, который не должен выполняться при возникновении исключения, заключаться в **попробуйте** блока. Исключения изнутри **попробуйте** запретить, используя **throw** инструкции и перехватываются за пределами **попробуйте** блок с одним или несколькими **catch**инструкций.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавление связанного **catch** блока.  
  
-   Попробуйте использовать **наконец** блокировать вместо **catch** блока.  
  
## <a name="see-also"></a>См. также  
 [Try... catch... finally инструкции](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)