---
title: Функция CvCreateDefaultMarkerSeriesOfDefaultProvider | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a13174b2991b7c69535a6d1910f761890397818
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552698"
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
 `ppProvider` Адрес переменной объекта поставщика. Адрес не может принимать значение NULL, переменная может содержать любое значение.

 `ppMarkerSeries` Адрес переменной объекта набора маркеров. Адрес не может принимать значение NULL, переменная может содержать любое значение.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если поставщик и набор маркеров были успешно созданы, или код ошибки в том случае, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)