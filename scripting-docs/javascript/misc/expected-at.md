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
ms.openlocfilehash: aa2728306d9e650bf7f8b446b6af5a409a39d0e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101565"
---
# <a name="expected-"></a>Ожидалось "\@"
Предпринята попытка создать переменную для использования с операторами условной компиляции с помощью `@set` инструкции, но не поместил знак "**@**" перед именем переменной.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте знак "**@**" непосредственно перед именем переменной. Пример:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>См. также  
 [@set Инструкции](../../javascript/reference/at-set-statement-javascript.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)
