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
ms.openlocfilehash: d100b7ff37ea5a3cd224fd420f14e4cb23061903
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630201"
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
 `pMarkerSeries` Адрес переменной объекта поставщика. Адрес не может принимать значение NULL, переменная может содержать любое значение.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если набор маркеров успешно освобожден, или код ошибки, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)