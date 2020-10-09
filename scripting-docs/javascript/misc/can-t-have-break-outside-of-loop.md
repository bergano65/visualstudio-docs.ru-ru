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
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862796"
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
 [Оператор break](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Управление ходом выполнения программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Устранение неполадок в скриптах](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)