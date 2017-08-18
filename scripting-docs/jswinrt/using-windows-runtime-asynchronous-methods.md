---
title: "Использование асинхронных методов среды выполнения Windows | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---
# <a name="using-windows-runtime-asynchronous-methods"></a>Использование асинхронных методов среды выполнения Windows
Многие методы среды выполнения Windows, особенно те методы, выполнение которых может занимать много времени, являются асинхронными. Обычно эти методы возвращают асинхронное действие или асинхронную операцию (например, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` или `Windows.Foundation.IAsyncOperationWithProgress`). Эти методы представлены в JavaScript шаблоном [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434). Они возвращают объект Promise с функцией [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx), для которой требуется указать функцию `completed`, обрабатывающую результат в случае успешного выполнения операции. Если вы не хотите задавать обработчик ошибок, используйте функцию [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) вместо функции `then`.  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Примеры асинхронных методов  
 В следующем примере функция `then` использует параметр, представляющий итоговое значение метода `createResourceAsync`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 В данном случае при сбое метод `createResourceAsync` возвращает Promise-объект в состоянии ошибки, но не выдает исключение. Вы можете обработать ошибку следующим образом с помощью функции `then`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Если вы не хотите обрабатывать ошибку явным образом, но хотите, чтобы она выдавала исключение, вместо указанной функции можно воспользоваться функцией `done`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Кроме того, вы можете отобразить ход выполнения операции с помощью третьей функции.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Дополнительные сведения об асинхронном программировании см. в разделе [Асинхронное программирование в JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
