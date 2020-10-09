---
title: Ожидался объект | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862108"
---
# <a name="object-expected"></a>Ожидался объект
Предпринята попытка вызвать метод или свойство для объекта, тип которого отличается от типа `Object`, или передать аргумент, тип которого отличается от типа `Object`. Объект вызова этого типа должен иметь тип `Object`.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызывайте этот метод или свойство только для объектов типа `Object`.  
  
- Если ошибка связана с аргументом без объектов, передайте объект типа `Object`.  
  
- Проверьте, не вызывается ли вместо объекта типа `Object` неопределенная или пустая ссылка.  
  
     Такая ошибка возникает, например, в связи с аргументом myVar, указанном в следующем коде:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Вместо него можно использовать следующий код:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Объекты и массивы](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)