---
title: Функция CvReleaseProvider | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974050"
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
 `pProvider` Контекст поставщика. Не может принимать значение NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если поставщик успешно освобожден, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)