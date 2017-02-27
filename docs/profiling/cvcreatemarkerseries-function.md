---
title: "Функция CvCreateMarkerSeries | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA - метод"
  - "CvCreateMarkerSeriesW - метод"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция CvCreateMarkerSeries
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает набор меток для данного поставщика.  
  
## Синтаксис  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### Параметры  
 `pProvider`  
 Объект поставщика, уже инициализированный функцией CvInitProvider.  Не может принимать значение NULL.  
  
 `pSeriesName`  
 Имя набора маркеров.  Не может принимать значение null, но пустая строка разрешена.  
  
 `ppMarkerSeries`  
 Адрес выходной переменной, в которой будет храниться контекст набора маркеров.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если набор маркеров успешно создан, или код ошибки, если они были.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
 **Юникод:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)