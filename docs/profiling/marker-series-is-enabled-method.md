---
title: Метод marker_series::is_enabled | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e68ec76737308d9bc9478f4106420626389f5eeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917728"
---
# <a name="marker_seriesis_enabled-method"></a>Метод marker_series::is_enabled
Определяет, разрешен ли поставщик данным сеансом.

## <a name="syntax"></a>Синтаксис

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Параметры
 `_Importance` Уровень важности.

 `_Category` Категория.

## <a name="return-value"></a>Возвращаемое значение

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также
- [Класс marker_series](../profiling/marker-series-class.md)