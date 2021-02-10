---
title: Перечисление marker_importance | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1559dc6c5aa24c54465aee6d29f0745be6c897c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917818"
---
# <a name="marker_importance-enumeration"></a>Перечисление marker_importance
Представляет уровень важности маркера визуализатора параллелизма.

## <a name="syntax"></a>Синтаксис

```cpp
enum marker_importance;
```

## <a name="members"></a>Участники

### <a name="values"></a>Значения

|name|Описание|
|----------|-----------------|
|`critical_importance`|Указывает, что маркер имеет критическую важность.|
|`high_importance`|Указывает, что маркер имеет высокую важность.|
|`low_importance`|Указывает, что маркер имеет низкую важность.|
|`normal_importance`|Указывает, что маркер имеет обычную важность.|

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также
- [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)