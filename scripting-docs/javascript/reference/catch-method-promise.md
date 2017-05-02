---
title: "Метод catch (Promise) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Метод catch (Promise)
Позволяет указать, какое действие следует выполнить при отклонении объекта Promise.  
  
## Синтаксис  
  
```  
  
promise.catch(onRejected)  
```  
  
#### Параметры  
 `promise`  
 Обязательный.  Объект Promise.  
  
 `onRejected`  
 Обязательный.  Функция обработчика ошибок, которая будет выполняться при отклонении объекта Promise.  
  
## Заметки  
  
## Пример  
 В следующем примере кода первый вызов функции timeout возвращает значение через 5 000 мс.  В данном коде объект Promise отклоняется и выполняется функция обработчика ошибок.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]