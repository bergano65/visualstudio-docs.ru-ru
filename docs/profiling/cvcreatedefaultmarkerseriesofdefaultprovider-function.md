---
title: Функция CvCreateDefaultMarkerSeriesOfDefaultProvider | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c68c7870430033d9ff20b94f51e516038c9eba6
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749191"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Функция CvCreateDefaultMarkerSeriesOfDefaultProvider
Создает наборы маркеров по умолчанию поставщика по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```C  
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
 **Заголовок:** *cvmarkers.h*  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)