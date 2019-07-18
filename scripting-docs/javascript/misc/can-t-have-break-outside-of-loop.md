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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946632"
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