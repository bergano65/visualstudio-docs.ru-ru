---
title: «default» может использоваться только один раз в операторе «switch» | Документация Майкрософт
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
ms.openlocfilehash: 24162efcc720d9c0073f8a5799c6278b8d3c8c62
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107831"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Вы попытались использовать **по умолчанию** инструкции более одного раза в операторе switch. В ситуации по умолчанию всегда является последней инструкцией case в операторе switch (это по фамилиям).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите все лишние **по умолчанию** случае операторы из вашей `switch` инструкции (используйте в большинстве инструкция case одно значение по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также  
 [Оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)