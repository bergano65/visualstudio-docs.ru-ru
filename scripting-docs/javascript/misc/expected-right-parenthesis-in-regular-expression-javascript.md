---
title: Ожидалось ")" в регулярном выражении (JavaScript) | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802346"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ ")" (JavaScript)
Предпринята попытка создать захвата регулярного выражения, утверждение или группы, но не содержит закрывающую скобку. В регулярных выражениях круглые скобки применяются в различных целях. В основном они используются для записи вложенных выражений, чтобы указать утверждения, или группировать шаблоны таким образом, чтобы элементы, которые могут рассматриваться как единое целое, *, +,?, и т. д.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте крайний правый закрывающими круглыми скобками.  
  
    > [!NOTE]
    >  Если для сопоставления с одной круглыми скобками следует экранировать его обратную косую черту - \\(— при этом он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)