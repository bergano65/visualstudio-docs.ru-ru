---
title: IDiaPropertyStorage::ReadPropertyNames | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742872"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Извлекает соответствующие имена строк для заданных идентификаторов свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Параметры
 `cpropid`

окне Число идентификаторов свойств в `rgpropid`.

 `rgpropid`

окне Массив идентификаторов свойств, для которых необходимо получить имена (`PROPID` определен в Втипес. h как `ULONG`).

 `rglpwstrName`

[вход, выход] Массив имен свойств для заданных идентификаторов свойств. Массив должен быть предварительно выделен для хранения запрошенного числа имен свойств и должен содержать по крайней мере `cpropid``BSTR` строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Возвращаемые имена свойств должны быть освобождены (путем вызова функции `SysFreeString`), когда они больше не нужны.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)