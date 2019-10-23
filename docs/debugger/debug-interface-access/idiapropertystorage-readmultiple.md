---
title: 'Идиапропертистораже:: Реадмултипле | Документация Майкрософт'
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
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742887"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Считывает указанные свойства из текущего набора свойств.

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

окне Число свойств, указанных в массиве `rgpspec`. Если значение равно нулю, метод не возвращает свойства, но возвращает `S_OK` как код успешного выполнения.

 `rgpspec`

окне Массив свойств для чтения. Свойства могут быть заданы либо с помощью идентификатора свойства, либо с помощью необязательного имени строки. Нет необходимости указывать свойства в каком-либо определенном порядке в массиве. Массив может содержать дублирующиеся свойства, что приводит к дублированию значений свойств при возврате для простых свойств. Непростые свойства должны возвращать отказ в доступе при попытке открыть их во второй раз. Массив может содержать сочетание идентификаторов свойств и строковых идентификаторов. Этот массив должен содержать по крайней мере `cpspec` число значений свойств.

 `rgvar`

[вход, выход] Массив структур `PROPVARIANT` (в пространстве имен Microsoft. VisualStudio. OLE. Interop), которые должны быть заполнены значениями для каждого свойства. Размер массива должен быть не менее `cpspec` элементов. Вызывающему объекту не нужно инициализировать значения в массиве.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если одно или несколько свойств не были найдены. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Если свойство не найдено, соответствующая запись в массиве `rgvar` содержит `VARIANT` с типом `VT_EMPTY`.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)