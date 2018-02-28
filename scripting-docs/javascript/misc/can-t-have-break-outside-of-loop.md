---
title: "CAN &#39; имеют t &#39; разрыв &#39; вне цикла | Документы Microsoft"
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>CAN &#39; имеют t &#39; разрыв &#39; вне цикла
Предпринята попытка использования **разрыв** ключевое слово за пределами цикла. **Разрыв** ключевое слово используется для завершения цикла или `switch` инструкции. Должны быть внедрены в теле цикла или `switch` инструкции. Тем не менее **метка** можно использовать ключевое слово break.  
  
```  
break labelname;  
```  
  
 Требуется только с меткой форме **разрыв** ключевое слово, если используются вложенные циклы или `switch` инструкций, а также для выхода из цикла, не является внутренней.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что **разрыв** ключевое слово появляется внутри внешнего цикла или коммутатора оператора.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)