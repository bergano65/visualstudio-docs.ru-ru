---
title: Функция CvCreateMarkerSeriesWithCodePageA | Документы Майкрософт
description: В этой статье приводятся справочные сведения о функции CvCreateMarkerSeriesWithCodePageA из пакета SDK визуализатора параллелизма (библиотека C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18e3367199154626703b671820d8d19d303630be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941025"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Функция CvCreateMarkerSeriesWithCodePageA
Создает набор маркеров для заданного поставщика и указывает кодовую страницу. Эту функцию можно использовать, чтобы явно указать кодовую страницу для текста ANSI, считанного с помощью функций API. Установка кодовой страницы может оказаться полезной в том случае, если трассировка сначала собирается, а затем анализируется на различных компьютерах с различными языковыми стандартами и языками. По умолчанию используется кодовая страница, возвращаемая функцией GetACP().

## <a name="syntax"></a>Синтаксис

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Параметры
 `pProvider` Объект поставщика, уже инициализированный функцией CvInitProvider. Не может быть NULL.

 `pSeriesName` Имя набора маркеров. Не может принимать значение NULL, но пустая строка разрешена.

 `nTextCodePage` Допустимая кодовая страница.

 `ppMarkerSeries` Адрес выходной переменной, в которой будет храниться контекст набора маркеров. Не может быть NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если набор маркеров успешно создан, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)