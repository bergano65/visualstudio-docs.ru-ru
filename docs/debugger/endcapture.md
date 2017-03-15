---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Завершает интервал захвата, который был запущен `BeginCapture`.  
  
## Синтаксис  
  
```cpp  
void EndCapture();  
```  
  
## Примечания  
 Обычно интервал захвата распространятся на подмножество одного кадра, например, при необходимости фиксировать данные графики только определенного типа вызова рисования.  Если интервал захвата распространяется на вызов к настоящему моменту, то захватываются два кадра графических данных.  Первый кадр расположен в интервале между вызовом `BeginCapture` и обращением к настоящему моменту; второй кадр расположен в интервале между первым событием Direct3D после обращения к настоящему моменту и вызовом `EndCapture`.  
  
 Для захвата интервала необходимо подготовить приложение для захвата и записи данных графики — необходимо вызвать метод [Init](../debugger/init.md) с помощью экземпляра класса `VsgDbg` перед вызовом `BeginCapture` или `EndCapture`.  
  
## См. также  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)