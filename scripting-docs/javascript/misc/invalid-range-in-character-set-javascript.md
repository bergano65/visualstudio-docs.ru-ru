---
title: Недопустимый диапазон в наборе символов (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29f28f0ceeb6bd1bf0a8f28438afd803d3a9a9ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576623"
---
# <a name="invalid-range-in-character-set-javascript"></a>Недопустимый диапазон в наборе символов (JavaScript)
Предпринята попытка создать регулярное выражение с недопустимым диапазоном наборов символов. Наборы символов должны находиться в диапазоне от одного символа, например a – z или 0-9; в набор символов нельзя включать классы символов, например \w. Первый символ в диапазоне должен также располагаться перед вторым символом в диапазоне. Например:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Чтобы составить набор символов регулярного выражения, используйте только один символ и убедитесь, что они находятся в правильном порядке.  
  
## <a name="see-also"></a>См. также:  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)