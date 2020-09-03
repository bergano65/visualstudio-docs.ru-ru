---
title: "\"default\" может использоваться в операторе \"Switch\" только один раз | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 0fdce6a86665b942098e4542dc237bc1ef22ad8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815517"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Предпринята попытка использовать инструкцию **по умолчанию** более одного раза в операторе switch. Регистр по умолчанию всегда является последним оператором case в операторе switch (он является переделами).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите все лишние операторы Case **по умолчанию** из `switch` инструкции (используйте не более одного оператора case по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также раздел  
 [Оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление ходом выполнения программы](../../javascript/controlling-program-flow-javascript.md)   
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)