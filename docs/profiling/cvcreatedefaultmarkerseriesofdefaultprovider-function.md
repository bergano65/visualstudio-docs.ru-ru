---
title: "Функция CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider - метод"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция CvCreateDefaultMarkerSeriesOfDefaultProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает серии маркеров по умолчанию для поставщика по умолчанию.  
  
## Синтаксис  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Параметры  
 `ppProvider`  
 Адрес переменной объекта поставщика.  Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
 `ppMarkerSeries`  
 Адрес переменной объекта серии маркеров.  Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
## Возвращаемое значение  
 S\_ОК, если провайдер и серия маркеров были успешно созданы или код ошибки в том случае, если какие\-либо ошибки были обнаружены.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)