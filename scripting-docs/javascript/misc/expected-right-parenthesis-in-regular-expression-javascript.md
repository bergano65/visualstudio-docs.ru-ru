---
title: "Ожидается &#39;) &#39; в регулярном выражении (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Ожидается &#39;) &#39; в регулярном выражении (JavaScript)
Предпринята попытка создать захвата регулярного выражения, утверждение или группы, но не содержит закрывающую скобку. Круглые скобки имеют несколько целей в регулярных выражениях. В основном они используются для записи вложенных выражений, для указания утверждений, или группировать шаблонов, чтобы элементы могут рассматриваться как единое целое, *, +,?, и т. д.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте правых закрывающей скобки.  
  
    > [!NOTE]
    >  Для сопоставления одной скобки следует экранировать его обратную косую черту - \\(-, чтобы он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)