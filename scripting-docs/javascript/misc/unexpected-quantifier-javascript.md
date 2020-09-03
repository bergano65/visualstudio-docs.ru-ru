---
title: Непредвиденный квантор (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815335"
---
# <a name="unexpected-quantifier-javascript"></a>Непредвиденный квантификатор (JavaScript)
При создании шаблона поиска регулярных выражений вы создали элемент шаблона с недопустимым коэффициентом повтора. Например, шаблон  
  
```js
/^+/  
```  
  
 является недопустимым, поскольку элемент ^ (начало ввода) не может иметь фактор повторения. В следующей таблице перечислены элементы, которые не могут иметь коэффициентов повторения.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|^|Начало входных данных|  
|$|Конец входных данных|  
|\b|Граница слова|  
|\B|Граница, не относящаяся к слову|  
|*|Ноль или более повторений|  
|+|Одно или несколько повторений|  
|?|Ноль или одно повторение|  
|\n|n повторений|  
|{n,}|n или более повторений|  
|{n, m}|От n до m повторений, включительно|  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что элемент шаблона поиска содержит только допустимые коэффициенты повторения.  
  
## <a name="see-also"></a>См. также раздел  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)