---
title: "Класс marker_series | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series - класс"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Класс marker_series
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Представляет последовательный канал событий, созданных одним поставщиком.  
  
## Синтаксис  
  
```  
class marker_series;  
```  
  
## Члены  
  
### Открытые конструкторы  
  
|Name|Описание|  
|----------|--------------|  
|[Конструктор marker\_series::marker\_series](../Topic/marker_series::marker_series%20Constructor.md)|Инициализирует новый экземпляр класса `marker_series`.|  
|[Деструктор marker\_series::~marker\_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Удаляет объект marker\_series и освобождает все выделенные ресурсы.|  
  
### Открытые методы  
  
|Name|Описание|  
|----------|--------------|  
|[Метод marker\_series::is\_enabled](../Topic/marker_series::is_enabled%20Method.md)|Определяет, разрешен ли поставщик данным сеансом.|  
|[Метод marker\_series::write\_alert](../profiling/marker-series-write-alert-method.md)|Записывает оповещение в файл трассировки визуализатора параллелизма.|  
|[Метод marker\_series::write\_flag](../profiling/marker-series-write-flag-method.md)|Записывает флаг в файл трассировки визуализатора параллелизма.|  
|[Метод marker\_series::write\_message](../profiling/marker-series-write-message-method.md)|Записывает сообщение в файл трассировки визуализатора параллелизма.|  
  
## Иерархия наследования  
 `marker_series`  
  
## Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## См. также  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)