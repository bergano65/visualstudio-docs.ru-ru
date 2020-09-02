---
title: Условная компиляция отключена | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816128"
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Предпринята попытка использовать переменную условной компиляции без предварительного включения условной компиляции. Включение условной компиляции означает, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор интерпретирует идентификаторы, начинающиеся с @, как переменные условной компиляции. Для этого необходимо начать условный код с помощью инструкции:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте следующий оператор в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также раздел  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Баланс](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Баланс](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Баланс](../../javascript/reference/at-set-statement-javascript.md)