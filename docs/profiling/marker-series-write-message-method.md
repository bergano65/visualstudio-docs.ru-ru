---
title: "Метод marker_series::write_message | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message - метод"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод marker_series::write_message
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает сообщение в файл трассировки визуализатора параллелизма.  
  
## Синтаксис  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
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
 Уровень Category.Importance.  
  
## Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## См. также  
 [Класс marker\_series](../profiling/marker-series-class.md)