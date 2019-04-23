---
title: Ожидается "]" в регулярном выражении (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c49ab90dae8f30dae075906bb9c7ecb7881428f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065081"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ "]" (JavaScript)
Предпринята попытка создать класс символов для сопоставления регулярного выражения, но отсутствует закрывающая квадратная скобка. Сочетания отдельных литеральный символ можно собрать в классы символов, поместив их в скобки. Класс символов соответствует любому знаку, содержащиеся в ней. Например / [abc] / соответствует любому из буквы «», «b» или «c».  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте закрывающую квадратную скобку регулярному выражению.  
  
    > [!NOTE]
    >  В соответствии с одна квадратная скобка следует экранировать его обратную косую черту - \\[-, он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)