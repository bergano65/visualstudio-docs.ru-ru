---
title: Функция CvIsEnabled | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92763e352d04d5aa3e88a68bad7adfcd05897027
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945418"
---
# <a name="cvisenabled-function"></a>Функция CvIsEnabled
Определяет, любому ли сеансу доступен указанный поставщик ETW.

## <a name="syntax"></a>Синтаксис

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>Параметры
 `category` Категория.

 `level` Уровень важности.

 `pProvider` Допустимый объект поставщика. Не может принимать значение NULL.

## <a name="return-value"></a>Возвращаемое значение
 Значение S_OK, если в данный момент поставщик доступен. Значение S_OK, если в данный момент поставщик недоступен. Код ошибки в том случае, если были какие-либо ошибки. Используйте макрос FAILED для проверки условия ошибки, а затем проверьте S_ОК/S_FALSE.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkers.h*

## <a name="see-also"></a>См. также
- [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)