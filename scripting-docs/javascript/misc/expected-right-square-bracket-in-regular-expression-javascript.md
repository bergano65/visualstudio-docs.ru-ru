---
title: Ожидался символ "]" в регулярном выражении (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815637"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ "]" (JavaScript)
Вы попытались создать класс символов для сопоставления регулярного выражения, но не включили правую квадратную скобку. Отдельные комбинации литеральных символов можно собрать в классы символов, поместив их в квадратные скобки. Класс символов соответствует любому символу, который он содержит. Например,/[abc]/соответствует любому из букв "a", "b" или "c".  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте правую квадратную скобку в регулярное выражение.  
  
    > [!NOTE]
    > Если нужно сопоставить одну квадратную скобку, построчно отменяйте ее с помощью обратной косой черты \\ [-, поэтому она не интерпретируется как Специальный символ [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>См. также раздел  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)