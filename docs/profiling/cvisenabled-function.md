---
title: "Функция CvIsEnabled | Microsoft Docs"
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
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled - метод"
  - "CvIsEnabledEx - метод"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Функция CvIsEnabled
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет, любому ли сеансу доступен указанный поставщик трассировки событий Windows.  
  
## Синтаксис  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### Параметры  
 `category`  
 Категория.  
  
 `level`  
 Уровень важности.  
  
 `pProvider`  
 Допустимый объект поставщика.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если в данный момент поставщик доступен.  S\_FALSE, если в настоящее время поставщик недоступен.  Код ошибки в том случае, если были какие\-либо ошибки.  Используйте макрос FAILED для проверки условия ошибки, а затем проверьте S\_ОК\/S\_FALSE.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)