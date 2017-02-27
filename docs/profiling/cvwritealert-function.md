---
title: "Функция CvWriteAlert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW - метод"
  - "CvWriteAlertA - метод"
  - "CvWriteAlertVA - метод"
  - "CvWriteAlertW - метод"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция CvWriteAlert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает оповещение в файл трассировки визуализатора параллелизма.  
  
## Синтаксис  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Параметры  
 `argList`  
 Список аргументов.  
  
 `pMarkerSeries`  
 Допустимый контекст метки ряда.  Не может принимать значение NULL.  
  
 `pMessage`  
 Строка форматирования сообщений.  Не может принимать значение NULL.  
  
## Возвращаемое значение  
 S\_ОК, если сообщение успешно записано.  Код ошибки в том случае, если были какие\-либо ошибки.  Используйте макрос SUCCEEDED\/FAILED для проверки условия ошибки.  
  
## Требования  
 **Заголовок:** cvmarkers.h  
  
 **Юникод:** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA, CvWriteAlertVA  
  
## См. также  
 [Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)