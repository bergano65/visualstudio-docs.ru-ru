---
title: «Break» не может располагаться вне цикла | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086701"
---
# <a name="cant-have-break-outside-of-loop"></a>break не может располагаться вне цикла
Вы попытались использовать **break** ключевое слово вне цикла. **Break** ключевое слово используется для завершения цикла или `switch` инструкции. Он должны быть внедрены в теле цикла или `switch` инструкции. Тем не менее **метка** можно следовать ключевое слово break.  
  
```js
break labelname;  
```  
  
 Требуется только с меткой виде **break** ключевое слово, если используются вложенные циклы или `switch` инструкций и вам необходимо разорвать цикл, который не является самой внутренней.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что **break** ключевое слово встречается внутри включающего цикл или оператор switch.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)