---
title: "Использование асинхронных методов среды выполнения Windows | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, асинхронные методы среды выполнения Windows"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Использование асинхронных методов среды выполнения Windows
Многие методы среды выполнения Windows, особенно те методы, выполнение которых может занимать много времени, являются асинхронными.  Обычно эти методы возвращают асинхронное действие или асинхронную операцию \(например, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` или `Windows.Foundation.IAsyncOperationWithProgress`\).  Эти методы также представлены в JavaScript шаблоном [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434).  Они возвращают Promise\-объект с функцией [then](http://msdn.microsoft.com/ru-ru/c63904fc-465b-4fd5-a1d6-e4fb200248e7), для которой требуется указать функцию `completed`, обрабатывающую результат в случае успешного выполнения операции.  Если вы не хотите задавать обработчик ошибок, следует использовать вместо функции [then](http://msdn.microsoft.com/ru-ru/c63904fc-465b-4fd5-a1d6-e4fb200248e7) функцию [done](http://msdn.microsoft.com/ru-ru/9a5e6877-a2cf-421f-a91e-37d84ccb40da).  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## Примеры асинхронных методов  
 В следующем примере функция [then](http://msdn.microsoft.com/ru-ru/c63904fc-465b-4fd5-a1d6-e4fb200248e7) использует параметр, представляющий итоговое значение метода `createResourceAsync`.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 В данном случае при сбое метод `createResourceAsync` возвращает Promise\-объект в состоянии ошибки, но не выдает исключение.  Вы можете обработать ошибку следующим образом с помощью функции [then](http://msdn.microsoft.com/ru-ru/c63904fc-465b-4fd5-a1d6-e4fb200248e7).  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Если вы не хотите обрабатывать ошибку явным образом, но хотите, чтобы она выдавала исключение, вместо указанной функции можно воспользоваться функцией [done](http://msdn.microsoft.com/ru-ru/9a5e6877-a2cf-421f-a91e-37d84ccb40da).  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Кроме того, вы можете отобразить ход выполнения операции с помощью третьей функции.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
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
  
 Дополнительные сведения об асинхронном программировании см. в разделе [Asynchronous programming](http://msdn.microsoft.com/ru-ru/904ff97c-bb36-4ac5-9eda-a961e3639415).  
  
## См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)