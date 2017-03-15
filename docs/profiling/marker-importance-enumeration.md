---
title: "Перечисление marker_importance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance - перечисление"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Перечисление marker_importance
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Представляет уровень важности метки визуализатора параллелизма.  
  
## Синтаксис  
  
```  
enum marker_importance;  
```  
  
## Члены  
  
### Значения  
  
|Name|Описание|  
|----------|--------------|  
|`critical_importance`|Указывает, что маркер имеет критическую важность.|  
|`high_importance`|Указывает, что маркер имеет высокую важность.|  
|`low_importance`|Указывает, что маркер имеет низкую важность.|  
|`normal_importance`|Указывает, что маркер имеет обычную важность.|  
  
## Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## См. также  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)