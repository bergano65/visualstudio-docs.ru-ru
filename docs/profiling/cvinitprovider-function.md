---
title: "Функция CvInitProvider | Microsoft Docs"
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
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider - метод"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Функция CvInitProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Инициализирует поставщика маркера.  Должен быть вызван перед любой другой функцией пакета SDK визуализатора параллелизма.  
  
## Синтаксис  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### Параметры  
 `pGuid`  
 GUID поставщика.  Не может принимать значение NULL.  
  
 `ppProvider`  
 Адрес выходной переменной, в которой будет храниться контекст поставщика.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК в случае, если поставщик будет успешно инициализирован, или код ошибки в случае, если возникла какая\-либо ошибка.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)