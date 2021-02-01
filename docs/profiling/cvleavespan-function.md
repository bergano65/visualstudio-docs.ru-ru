---
title: Функция CvLeaveSpan | Документы Майкрософт
description: В этой статье приводятся справочные сведения о функции CvLeaveSpan из пакета SDK визуализатора параллелизма (библиотека C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1dcd98a8233f8080d03650c3989805ee9ec7289
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686588"
---
# <a name="cvleavespan-function"></a>Функция CvLeaveSpan
Отмечает конец диапазона.

## <a name="syntax"></a>Синтаксис

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Параметры
 `pSpan` Объект диапазона, возвращенный во время предыдущего вызова CvEnterSpan*. Не может быть NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если сообщение успешно записано. Код ошибки в том случае, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)