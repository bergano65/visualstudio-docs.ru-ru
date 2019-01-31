---
title: Функция CvReleaseMarkerSeries | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bfa9952a834110ef0fea36568ea210b637547aa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794139"
---
# <a name="cvreleasemarkerseries-function"></a>Функция CvReleaseMarkerSeries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Освобождает набор маркеров. Не используйте объект набора маркеров после освобождения, в противном случае приложение может завершиться аварийно. Сбой при освобождении набора маркеров приводит к утечке памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMarkerSeries`  
 Адрес переменной объекта поставщика. Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если набор маркеров успешно освобожден, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
## <a name="see-also"></a>См. также раздел  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)
