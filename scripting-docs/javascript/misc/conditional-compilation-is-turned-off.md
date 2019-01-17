---
title: Условная компиляция отключена | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092889"
---
# <a name="conditional-compilation-is-turned-off"></a>Условная компиляция отключена
Вы попытались использовать переменные условной компиляции без первого включение условной компиляции на. Включение условной компиляции сообщает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор интерпретировать идентификаторы, начинающиеся с, как переменные условной компиляции. Это можно сделать, начиная с оператором условного кода:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте следующую инструкцию в начало условного кода:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Инструкции](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Инструкции](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Оператор](../../javascript/reference/at-set-statement-javascript.md)