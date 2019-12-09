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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572938"
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Предпринята попытка использовать переменную условной компиляции без предварительного включения условной компиляции. Включение условной компиляции означает, что компилятор [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] интерпретирует идентификаторы, начинающиеся с @, как переменные условной компиляции. Для этого необходимо начать условный код с помощью инструкции:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте следующий оператор в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также:  
   [условной компиляции](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on  инструкции](../../javascript/reference/at-cc-on-statement-javascript.md)  
 [@if  инструкции](../../javascript/reference/at-if-statement-javascript.md)  
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)