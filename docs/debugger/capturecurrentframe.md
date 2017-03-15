---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает оставшуюся часть текущего кадра в файл журнала графики.  
  
## Синтаксис  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Примечания  
 Если выполняется другой захват в данный момент — например, запущенный `BeginCapture`, — захват завершается и записывается в журнал графики как отдельный кадр.  Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр.  Окончание текущего кадра отмечено вызовом к настоящему моменту.  
  
 Для захвата кадра необходимо подготовить приложение для захвата и записи данных графики — необходимо вызвать метод [Init](../debugger/init.md) с помощью экземпляра класса `VsgDbg` перед вызовом `CaptureCurrentFrame`.  
  
## См. также  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)