---
title: "Обработка событий среды выполнения Windows на языке JavaScript | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Обработка событий среды выполнения Windows на языке JavaScript
В JavaScript события среды выполнения Windows представлены иначе, чем в C++ или .NET Framework. Они не являются свойствами класса, а представляются в виде строковых идентификаторов, которые передаются в методы класса `addEventListener` и `removeEventListener`. Например, можно добавить обработчик событий для события [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx), передав строку "positionchanged" в метод `Geolocator.addEventListener`:  
  
```JavaScript  
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
  
 В JavaScript аргументы событий среды выполнения Windows представлены в виде отдельного объекта событий. В следующем примере метода обработчика событий параметр `ev` является объектом, который содержит как отправителя (целевое свойство), так и другие аргументы событий. Аргументами событий являются те аргументы, которые задокументированы для каждого из событий.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## <a name="see-also"></a>См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)