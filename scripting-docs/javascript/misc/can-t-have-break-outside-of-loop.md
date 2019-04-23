---
title: «Break» не может располагаться вне цикла | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: a02848230187eb465d56ed73e44380e4b043b117
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084431"
---
# <a name="cant-have-break-outside-of-loop"></a>break не может располагаться вне цикла
Вы попытались использовать **break** ключевое слово вне цикла. **Break** ключевое слово используется для завершения цикла или `switch` инструкции. Он должны быть внедрены в теле цикла или `switch` инструкции. Тем не менее **метка** можно следовать ключевое слово break.  
  
```js
break labelname;  
```  
  
 Требуется только с меткой виде **break** ключевое слово, если используются вложенные циклы или `switch` инструкций и вам необходимо разорвать цикл, который не является самой внутренней.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что **break** ключевое слово встречается внутри включающего цикл или оператор switch.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)