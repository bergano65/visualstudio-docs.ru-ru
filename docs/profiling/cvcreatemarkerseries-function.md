---
title: Функция CvCreateMarkerSeries | Документы Майкрософт
description: В этой статье приводятся справочные сведения о функции CvCreateMarkerSeries из пакета SDK визуализатора параллелизма (библиотека C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941038"
---
# <a name="cvcreatemarkerseries-function"></a>Функция CvCreateMarkerSeries
Создает набор маркеров для данного поставщика.

## <a name="syntax"></a>Синтаксис

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Параметры
 `pProvider` Объект поставщика, уже инициализированный функцией CvInitProvider. Не может быть NULL.

 `pSeriesName` Имя набора маркеров. Не может принимать значение NULL, но пустая строка разрешена.

 `ppMarkerSeries` Адрес выходной переменной, в которой будет храниться контекст набора маркеров. Не может быть NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если набор маркеров успешно создан, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

 **Юникод:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)