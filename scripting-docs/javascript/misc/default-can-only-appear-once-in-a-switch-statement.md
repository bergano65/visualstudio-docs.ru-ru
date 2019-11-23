---
title: "\"default\" может использоваться в операторе \"Switch\" только один раз | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90652e44a4bd0362f679be71d0d6401165487aec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572879"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Предпринята попытка использовать инструкцию **по умолчанию** более одного раза в операторе switch. Регистр по умолчанию всегда является последним оператором case в операторе switch (он является переделами).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите все лишние операторы Case **по умолчанию** из оператора `switch` (используйте не более одного оператора case по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также:  
 [оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление  последовательности программ](../../javascript/controlling-program-flow-javascript.md)  
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)