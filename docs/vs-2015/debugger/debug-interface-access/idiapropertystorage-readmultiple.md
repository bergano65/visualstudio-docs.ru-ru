---
title: IDiaPropertyStorage::ReadMultiple | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538087"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Чтение указанного свойства из текущего набора свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Параметры
 `cpspec`

[in] Число свойств, указанных в `rgpspec` массива. Если значение равно нулю, метод возвращает нет свойств, но возвращает `S_OK` как код успешного выполнения.

 `rgpspec`

[in] Массив свойств для чтения. Свойства могут быть указаны с Идентификатором свойства объекта или имени необязательная строка. Это не требуется указывать свойства в определенном порядке в массиве. Массив может содержать повторяющиеся свойства, что повторяющиеся значения при возвращении для простых свойств. Свойства non-simple должны возвращать отказано в доступе при попытке открыть их еще раз. Массив может содержать смесь идентификаторы свойств и строковых идентификаторов. Этот массив должен иметь по крайней мере `cpspec` число значений свойств.

 `rgvar`

[in, out] Массив `PROPVARIANT` структуры (в пространстве имен Microsoft.VisualStudio.OLE.Interop), который подлежит заполнению значения для каждого свойства. Размер массива должен быть по крайней мере `cpspec` элементов в размер. Вызывающему объекту не требуется для инициализации значений в массиве.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если один или несколько свойств не найден. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Если свойство не найдено, соответствующая запись в `rgvar` массив содержит `VARIANT` с типом `VT_EMPTY`.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)