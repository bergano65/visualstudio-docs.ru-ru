---
title: Обработка событий среды выполнения Windows на языке JavaScript | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302817"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Обработка событий среды выполнения Windows на языке JavaScript
В JavaScript события среды выполнения Windows представлены иначе, чем в C++ или .NET Framework. Они не являются свойствами класса, а представляются в виде строковых идентификаторов (в нижнем регистре), которые передаются в методы класса `addEventListener` и `removeEventListener`. Например, можно добавить обработчик событий для события [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx), передав строку "positionchanged" в метод `Geolocator.addEventListener`:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Вы также можете задать свойство `locator.onpositionchanged`:  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Еще одно различие между .NET, C++ и JavaScript — это количество параметров, принимаемых обработчиком событий. В .NET и C++ обработчик принимает два параметра: отправитель события и данные события. В JavaScript они объединены в один объект `Event`. В следующем примере параметр `ev` содержит отправитель события (свойство `target`) и свойства данных события (здесь это просто `position`). Свойства данных событий — это свойства, которые задокументированы для каждого из событий.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## <a name="see-also"></a>См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
