---
title: В регулярном выражении ожидался символ ")" (JavaScript) | Документация Майкрософт
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
ms.openlocfilehash: 7c10449df9ef3331949695b7423da3eb08b65433
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577541"
---
# <a name="expected--in-regular-expression-javascript"></a>В регулярном выражении ожидался символ ")" (JavaScript)
Предпринята попытка создать запись регулярного выражения, утверждение или группу, но не включала закрывающая круглая скобка. В регулярных выражениях круглые скобки имеют несколько целей. В основном они используются для записи подвыражений, для указания утверждений или для объединения шаблонов вместе, чтобы элементы можно было рассматривать как одну единицу с помощью *, +,? и т. д.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Добавьте крайние правые закрывающие скобки.  
  
    > [!NOTE]
    > Если нужно сопоставить одну круглую скобку, заключите ее в обратную косую черту \\ (так что она не интерпретируется как Специальный символ путем [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)    
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)