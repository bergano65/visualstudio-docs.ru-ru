---
title: Функция CvReleaseMarkerSeries | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51ef7cc83c876f5ac9031010fd45e2230e6c4c03
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007007"
---
# <a name="cvreleasemarkerseries-function"></a>Функция CvReleaseMarkerSeries
Освобождает набор маркеров. Не используйте объект набора маркеров после освобождения, в противном случае приложение может завершиться аварийно. Сбой при освобождении набора маркеров приводит к утечке памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C  
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
 **Заголовок:** *cvmarkers.h*  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)