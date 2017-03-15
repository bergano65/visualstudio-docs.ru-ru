---
title: "Функция CvCreateMarkerSeriesWithCodePageA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA - метод"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция CvCreateMarkerSeriesWithCodePageA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создает набор маркеров для заданного поставщика и указывает кодовую страницу.  Эту функцию можно использовать, чтобы явно указать кодовую страницу для текста ANSI, считанного с помощью функций API.  Установка кодовой страницы может оказаться полезной в том случае, если трассировка сначала собирается, а затем анализируется на различных компьютерах с различными языковыми стандартами и языками.  По умолчанию используется кодовая страница, возвращаемая функцией GetACP\(\).  
  
## Синтаксис  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Параметры  
 `pProvider`  
 Объект поставщика, уже инициализированный функцией CvInitProvider.  Не может принимать значение NULL.  
  
 `pSeriesName`  
 Имя набора маркеров.  Не может принимать значение null, но пустая строка разрешена.  
  
 `nTextCodePage`  
 Допустимая кодовая страница.  
  
 `ppMarkerSeries`  
 Адрес выходной переменной, в которой будет храниться контекст набора маркеров.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если набор маркеров успешно создан, или код ошибки, если они были.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)