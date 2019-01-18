---
title: Недопустимый диапазон в символе задайте (JavaScript) | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346089"
---
# <a name="invalid-range-in-character-set-javascript"></a>Недопустимый диапазон в наборе символов (JavaScript)
Предпринята попытка создать регулярное выражение с диапазоном набора недопустимый символ. Наборов символов должно находиться в диапазоне от одного символа, например, a – z или 0-9; Классы символов, таких как \w нельзя включить в набор символов. Первый символ в диапазоне, также должны следовать после второго знака в диапазоне. Пример:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Используйте только одиночные символы для составления ваш набор символов регулярного выражения и убедитесь, что они находятся в правильном порядке.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)