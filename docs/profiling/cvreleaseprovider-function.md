---
title: Функция CvReleaseProvider | Документы Майкрософт
description: В этой статье приводятся справочные сведения о функции CvReleaseProvider из пакета SDK визуализатора параллелизма (библиотека C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948235"
---
# <a name="cvreleaseprovider-function"></a>Функция CvReleaseProvider
Освобождает поставщик маркеров. Освобождение поставщика маркеров не повлияет на ранее созданный набор маркеров данного поставщика. Наборы маркеров должны быть выпущены раздельно вызовом функции CvReleaseMarkerSeries. Сбой при освобождении поставщика маркеров приводит к утечке памяти.

## <a name="syntax"></a>Синтаксис

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Параметры
 `pProvider` Контекст поставщика. Не может быть NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если поставщик успешно освобожден, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)