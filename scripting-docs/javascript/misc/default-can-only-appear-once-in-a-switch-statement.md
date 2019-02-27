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
ms.openlocfilehash: a5d31a74900e8eee5daa97bb7f9af5146b237e04
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842186"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Вы попытались использовать **по умолчанию** инструкции более одного раза в операторе switch. В ситуации по умолчанию всегда является последней инструкцией case в операторе switch (это по фамилиям).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалите все лишние **по умолчанию** случае операторы из вашей `switch` инструкции (используйте в большинстве инструкция case одно значение по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также  
 [Оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)