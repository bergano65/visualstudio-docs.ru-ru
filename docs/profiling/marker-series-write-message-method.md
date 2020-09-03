---
title: Метод marker_series::write_message | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a4cb4a604907908b8f2b35ea0baa583ab1ca57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328312"
---
# <a name="marker_serieswrite_message-method"></a>Метод marker_series::write_message
Записывает сообщение в файл трассировки визуализатора параллелизма.

## <a name="syntax"></a>Синтаксис

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Параметры
 `_Format` Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.

 `_Importance` Уровень важности.

 `_Category` Категория. Уровень важности.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также
- [Класс marker_series](../profiling/marker-series-class.md)