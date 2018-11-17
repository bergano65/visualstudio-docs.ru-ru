---
title: Функция CvReleaseMarkerSeries | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf62ece61be25ef92866a9b761819c842d9154c3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801528"
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
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)



