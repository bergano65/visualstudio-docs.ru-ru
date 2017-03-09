---
title: "VsgDbg::~VsgDbg (деструктор) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (деструктор)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Уничтожает экземпляр класса `VsgDbg`.  Если данные графики активно записываются, файл журнала графики завершается и закрывается, и ресурсы, которые использовались при активной записи данных графики, освобождаются.  
  
## Синтаксис  
  
```cpp  
~VsgDbg();  
```  
  
## См. также  
 [VsgDbg::VsgDbg \(конструктор\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)