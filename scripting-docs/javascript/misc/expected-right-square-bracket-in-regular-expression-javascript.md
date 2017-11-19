---
title: "Ожидается &#39;] &#39; в регулярном выражении (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Ожидается &#39;] &#39; в регулярном выражении (JavaScript)
Предпринята попытка создать класс символов для сопоставления регулярных выражений, но не содержит закрывающую квадратную скобку. Отдельный символ сочетаний можно собрать в классы символов, поместив их в квадратные скобки. Класс символов соответствует любому символу, он содержит. Например / [abc] / соответствует любому из символов «», «b» или «c».  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Добавьте закрывающую квадратную скобку регулярного выражения.  
  
    > [!NOTE]
    >  Если вы хотите соответствует одна квадратная скобка, экранировать его обратную косую черту - \\[, что он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)