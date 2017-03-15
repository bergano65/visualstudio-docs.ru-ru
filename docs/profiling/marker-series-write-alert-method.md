---
title: "Метод marker_series::write_alert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert - метод"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод marker_series::write_alert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает оповещение в файл трассировки визуализатора параллелизма.  
  
## Синтаксис  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Параметры  
 `_Format`  
 Строка составного формата, содержащая текст, который перемежается несколькими элементами форматирования \(или ни одним из них\), соответствующими объектам в списке аргументов.  
  
## Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## См. также  
 [Класс marker\_series](../profiling/marker-series-class.md)