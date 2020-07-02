---
title: "\"Break\" не может находиться вне цикла | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817662"
---
# <a name="cant-have-break-outside-of-loop"></a>break не может располагаться вне цикла
Предпринята попытка использовать ключевое слово **break** вне цикла. Ключевое слово **break** используется для завершения цикла или `switch` оператора. Он должен быть внедрен в тело цикла или `switch` оператора. Однако **Метка** может следовать за ключевым словом break.  
  
```js
break labelname;  
```  
  
 При использовании вложенных циклов или инструкций требуется только форма с метками с **меткой,** `switch` и необходимо разорвать цикл, который не является самым внутренним.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что ключевое слово **break** отображается внутри внешнего цикла или оператора switch.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление ходом выполнения программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)