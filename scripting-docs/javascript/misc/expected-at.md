---
title: Ожидался символ "@" | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814828"
---
# <a name="expected-"></a>Ожидался символ " \@ "
Предпринята попытка создать переменную, которая будет использоваться с инструкциями условной компиляции с помощью `@set` инструкции, но не поместит знак " **@** " перед именем переменной.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте знак at " **@** " непосредственно перед именем переменной. Пример:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>См. также  
 [@setБаланс](../../javascript/reference/at-set-statement-javascript.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)
