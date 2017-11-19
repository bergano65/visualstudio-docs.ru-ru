---
title: "Условная компиляция отключена | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Предпринята попытка использования переменной условной компиляции без первого включение условной компиляции в. Включение условной компиляции сообщает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор интерпретирует идентификаторы, начинающиеся с, как переменные условной компиляции. Это можно сделать, начиная с оператором условного кода:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте следующий оператор в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onИнструкции](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifИнструкции](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)