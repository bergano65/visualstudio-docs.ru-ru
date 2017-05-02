---
title: "Обработка событий среды выполнения Windows в JavaScript | Microsoft Docs"
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
  - "JavaScript, события среды выполнения Windows"
  - "события среды выполнения Windows [JavaScript]"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Обработка событий среды выполнения Windows в JavaScript
В JavaScript события среды выполнения Windows представлены иначе, чем в C\+\+ или .NET Framework.  Они не являются свойствами класса, а представляются в виде строковых идентификаторов, которые передаются в методы класса `addEventListener` и `removeEventListener`.  Например, вы можете добавить обработчик событий для события [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx), передав строку "positionchanged" в метод `Geolocator.addEventListener`:  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Вы также можете задать свойство `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 В JavaScript аргументы событий среды выполнения Windows представлены в виде отдельного объекта событий.  В следующем примере метода обработчика событий параметр `ev` является объектом, который содержит как отправителя \(целевое свойство\), так и другие аргументы событий.  Аргументами событий являются те аргументы, которые задокументированы для каждого из событий.  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)