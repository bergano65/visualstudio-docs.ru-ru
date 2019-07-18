---
title: Ожидалось ")" в регулярном выражении (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7daf5d876f68168ce0b58ea2cc9b52a309107bc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446531"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ ")" (JavaScript)
Предпринята попытка создать захвата регулярного выражения, утверждение или группы, но не содержит закрывающую скобку. В регулярных выражениях круглые скобки применяются в различных целях. В основном они используются для записи вложенных выражений, чтобы указать утверждения, или группировать шаблоны таким образом, чтобы элементы, которые могут рассматриваться как единое целое, *, +,?, и т. д.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте крайний правый закрывающими круглыми скобками.  
  
    > [!NOTE]
    > Если для сопоставления с одной круглыми скобками следует экранировать его обратную косую черту - \\(— при этом он интерпретируется как специальный символ, не [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)