---
title: "Функция CvReleaseProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider - метод"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция CvReleaseProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Выпускает поставщик маркера.  Выпуск поставщика маркеров не повлияет на ранее созданную серию маркеров данного поставщика.  Серии маркеров должны быть выпущены раздельно вызовом CvReleaseMarkerSeries.  Сбой при выпуске поставщика вызывает утечку памяти.  
  
## Синтаксис  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Параметры  
 `pProvider`  
 Контекст поставщика.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если поставщик успешно выпущен, или код ошибки в случае каких\-либо ошибок.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)