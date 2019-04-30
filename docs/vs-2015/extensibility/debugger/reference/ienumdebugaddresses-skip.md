---
title: IEnumDebugAddresses::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a150ab025221ddd22870082d9b8d08d044594856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572826"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Этот метод пропускает указанное число элементов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

#### <a name="parameters"></a>Параметры
 `celt`

 [in] Количество пропускаемых элементов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если `celt` больше, чем число оставшихся элементов; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если `celt` указывает значения, большего, чем остальных элементов, перечислению задается до конца и `S_FALSE` возвращается.

## <a name="see-also"></a>См. также
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)