---
title: Непредвиденный квантификатор (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f18195f344adca16fce7403d225c42826a2af544
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843407"
---
# <a name="unexpected-quantifier-javascript"></a>Непредвиденный квантификатор (JavaScript)
При создании шаблона регулярного выражения поиска, вы создали элемент шаблона с коэффициентом Недопустимое повторение. Например шаблон  
  
```js
/^+/  
```  
  
 не допускается из-за элемент ^ (в начале входных данных) не может иметь Коэффициент повторения. Ниже перечислены элементы, которые не могут иметь повторение факторов.  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|^|Начале входных данных|  
|$|Конец входных данных|  
|\b|Граница слова|  
|\B|Не на границе слова|  
|*|Ноль или более повторений|  
|+|Один или несколько повторений|  
|?|Ноль или один повторений|  
|{n}|n повторений|  
|{n,}|n или дополнительные повторений|  
|{n, m}|От n до m повторений, включительно|  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что элемент шаблона поиска содержит только факторов юридические повторение.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)