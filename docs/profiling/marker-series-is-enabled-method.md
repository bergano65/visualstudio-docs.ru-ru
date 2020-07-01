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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ff6b0449c877b5ae925ba2088917d7bacab4c34
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330670"
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