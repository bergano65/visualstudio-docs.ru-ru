---
title: «default» может использоваться только один раз в операторе «switch» | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803887"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>default может использоваться в операторе switch только один раз
Вы попытались использовать **по умолчанию** инструкции более одного раза в операторе switch. В ситуации по умолчанию всегда является последней инструкцией case в операторе switch (это по фамилиям).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалите все лишние **по умолчанию** случае операторы из вашей `switch` инструкции (используйте в большинстве инструкция case одно значение по умолчанию в операторе switch).  
  
## <a name="see-also"></a>См. также  
 [Оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)