---
title: "Функция CvCreateDefaultMarkerSeriesOfDefaultProvider | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3fae064fab478de88f6b5f66c41df7e4e57d4ead
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Функция CvCreateDefaultMarkerSeriesOfDefaultProvider
Создает наборы маркеров по умолчанию поставщика по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProvider`  
 Адрес переменной объекта поставщика. Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
 `ppMarkerSeries`  
 Адрес переменной объекта набора маркеров. Адрес не может принимать значение NULL, переменная может содержать любое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если поставщик и набор маркеров были успешно созданы, или код ошибки в том случае, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)