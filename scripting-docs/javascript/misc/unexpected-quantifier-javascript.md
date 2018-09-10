---
title: Непредвиденный квантификатор (JavaScript) | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282271"
---
# <a name="unexpected-quantifier-javascript"></a>Непредвиденный квантификатор (JavaScript)
При создании шаблона регулярного выражения поиска, вы создали элемент шаблона с коэффициентом Недопустимое повторение. Например шаблон  
  
```  
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
|{n}|n или дополнительные повторений|  
|{n, m}|От n до m повторений, включительно|  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что элемент шаблона поиска содержит только факторов юридические повторение.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)