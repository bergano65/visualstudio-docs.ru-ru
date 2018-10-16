---
title: Ожидается &#39;]&#39; в регулярном выражении (JavaScript) | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283721"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Ожидается &#39;]&#39; в регулярном выражении (JavaScript)
Предпринята попытка создать класс символов для сопоставления регулярного выражения, но отсутствует закрывающая квадратная скобка. Сочетания отдельных литеральный символ можно собрать в классы символов, поместив их в скобки. Класс символов соответствует любому знаку, содержащиеся в ней. Например / [abc] / соответствует любому из буквы «», «b» или «c».  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте закрывающую квадратную скобку регулярному выражению.  
  
    > [!NOTE]
    >  В соответствии с одна квадратная скобка следует экранировать его обратную косую черту - \\[-, он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)