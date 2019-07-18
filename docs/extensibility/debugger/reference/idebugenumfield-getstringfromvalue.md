---
title: IDebugEnumField::GetStringFromValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd7466e5390cff747532dca0343680cf359db46a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345088"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Этот метод получает имя константы перечисления, учитывая его значение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Параметры
`value`\
[in] Значение, для которого необходимо получить имя перечисления констант.

`pbstrValue`\
[out] Возвращает имя константы перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если значение не имеет связанного имени, либо возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если имеется несколько имен, связанный с тем же значением, возвращается имя определяется в перечислении.

## <a name="see-also"></a>См. также
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)