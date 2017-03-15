---
title: "Функция CvLeaveSpan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan - метод"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция CvLeaveSpan
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отмечает конец диапазона.  
  
## Синтаксис  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### Параметры  
 `pSpan`  
 Объект диапазона, возвращенный во время предыдущего вызова CvEnterSpan\*.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если сообщение успешно записано.  Код ошибки в том случае, если были какие\-либо ошибки.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)