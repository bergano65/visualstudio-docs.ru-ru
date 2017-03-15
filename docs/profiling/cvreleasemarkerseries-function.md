---
title: "Функция CvReleaseMarkerSeries | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries - метод"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция CvReleaseMarkerSeries
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Освобождает набор маркеров.  Не используйте объект набора маркеров после освобождения, в противном случае приложение может завершиться аварийно.  Сбой при освобождении набора маркеров приводит к утечке памяти.  
  
## Синтаксис  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### Параметры  
 `pMarkerSeries`  
 Адрес переменной объекта поставщика.  Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
## Возвращаемое значение  
 S\_ОК, если набор маркеров успешно освобожден, или код ошибки, если были какие\-либо ошибки.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)