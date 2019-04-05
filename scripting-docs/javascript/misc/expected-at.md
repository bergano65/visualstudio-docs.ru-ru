---
title: Ожидалось "@" | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da8eb2f21cbe7ef611aaba863e853a2fe7a71753
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018315"
---
# <a name="expected-"></a>Ожидалось "\@"
Предпринята попытка создать переменную для использования с операторами условной компиляции с помощью `@set` инструкции, но не поместил знак "**@**" перед именем переменной.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте знак "**@**" непосредственно перед именем переменной. Пример:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>См. также  
 [@set Инструкции](../../javascript/reference/at-set-statement-javascript.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)
