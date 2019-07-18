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
ms.openlocfilehash: 52b98875b560e4863a93849cf99c2f8756cd438a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005895"
---
# <a name="unexpected-quantifier-javascript"></a>Непредвиденный квантификатор (JavaScript)
При создании шаблона регулярного выражения поиска, вы создали элемент шаблона с коэффициентом Недопустимое повторение. Например шаблон  
  
```js
/^+/  
```  
  
 не допускается из-за элемент ^ (в начале входных данных) не может иметь Коэффициент повторения. Ниже перечислены элементы, которые не могут иметь повторение факторов.  
  
|Элемент|Описание|  
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
  
- Убедитесь, что элемент шаблона поиска содержит только факторов юридические повторение.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)