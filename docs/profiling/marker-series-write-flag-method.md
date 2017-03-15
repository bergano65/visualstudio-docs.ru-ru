---
title: "Метод marker_series::write_flag | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag - метод"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод marker_series::write_flag
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает флаг в файл трассировки визуализатора параллелизма.  
  
## Синтаксис  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Параметры  
 `_Format`  
 Строка составного формата, содержащая текст, который перемежается несколькими элементами форматирования \(или ни одним из них\), соответствующими объектам в списке аргументов.  
  
 `_Importance`  
 Уровень важности.  
  
 `_Category`  
 Категория.  
  
## Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## См. также  
 [Класс marker\_series](../profiling/marker-series-class.md)