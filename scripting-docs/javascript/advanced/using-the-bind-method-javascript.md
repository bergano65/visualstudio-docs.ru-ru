---
title: "Использование метода bind (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c49f6e8c5606845f41cc947029ac9405f97665f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-bind-method-javascript"></a>Использование метода bind (JavaScript)
Метод `bind` языка JavaScript используется в ряде случаев. Обычно он применяется, чтобы сохранить контекст выполнения для функции, выполняемой в другом контексте. `bind` создает новую функцию с тем же телом, что и у исходной функции. Первый передаваемый в `bind` аргумент задает значение ключевого слова `this` в привязанной функции. Можно также передать в `bind` дополнительные необязательные аргументы. Примеры других использований см. в разделе [Метод bind (Function)](../../javascript/reference/bind-method-function-javascript.md). Пример использования `bind` для частичного применения функций см. в статье [Советы и шаблоны асинхронного программирования в приложении Hilo на JavaScript (Магазин Windows)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Сохранение контекста выполнения с помощью привязки  
 Функция `bind` часто используется при добавлении прослушивателей событий. В следующем примере кода с помощью функции `bind` сохраняется контекст текущего объекта (`DataObject`). Объект данных передается в функцию `bind` с помощью ключевого слова `this`, которое предоставляет доступ к свойствам и функциям объекта данных при выполнении обработчика событий `dataReadyHandler`. Чтобы показать, как работает функция `bind`, этот код создает пользовательское событие.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);  
}  
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Если поместить строку кода с функцией `bind` в комментарии, вынести за комментарии строку кода, которая вызывает `addEventListener` без `bind`, а затем повторно выполнить код, выполнение функции `dataReadyHandler` завершится сбоем. Например, в `dataReadyHander` будет не определен объект `this.name`, и выполнение метода `this.data()` завершится ошибкой, поскольку объект `this` больше не будет ссылаться на объект данных.  
  
## <a name="see-also"></a>См. также  
 [Метод bind (Function)](../../javascript/reference/bind-method-function-javascript.md)