---
title: Условная компиляция отключена | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8317121b840d82ab12d4a9e1ca50f6680eb1e21d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946580"
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Вы попытались использовать переменные условной компиляции без первого включение условной компиляции на. Включение условной компиляции сообщает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор интерпретировать идентификаторы, начинающиеся с, как переменные условной компиляции. Это можно сделать, начиная с оператором условного кода:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте следующую инструкцию в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Инструкции](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Инструкции](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)