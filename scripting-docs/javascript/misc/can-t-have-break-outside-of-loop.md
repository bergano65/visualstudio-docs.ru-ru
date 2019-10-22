---
title: "\"Break\" не может находиться вне цикла | Документация Майкрософт"
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576022"
---
# <a name="cant-have-break-outside-of-loop"></a>break не может располагаться вне цикла
Предпринята попытка использовать ключевое слово **break** вне цикла. Ключевое слово **break** используется для завершения цикла или оператора `switch`. Он должен быть внедрен в тело цикла или оператора `switch`. Однако **Метка** может следовать за ключевым словом break.  
  
```js
break labelname;  
```  
  
 Если используются вложенные циклы или `switch` операторы и необходимо разорвать цикл, который не является самым внутренним, требуется только форма с меткой.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что ключевое слово **break** отображается внутри внешнего цикла или оператора switch.  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление   последовательности программ](../../javascript/controlling-program-flow-javascript.md)  
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)