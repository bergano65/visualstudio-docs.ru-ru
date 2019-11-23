---
title: Ожидался символ "@" | Документация Майкрософт
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
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576513"
---
# <a name="expected-"></a>Требуется "\@"
Предпринята попытка создать переменную, которая будет использоваться с инструкциями условной компиляции с помощью оператора `@set`, но не поместит знак " **@** " перед именем переменной.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте знак at " **@** " непосредственно перед именем переменной. Например:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>См. также:  
 [@set  инструкции](../../javascript/reference/at-set-statement-javascript.md)  
   [условной компиляции](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)
