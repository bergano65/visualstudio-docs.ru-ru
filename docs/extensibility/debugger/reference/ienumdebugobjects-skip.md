---
title: IEnumDebugОбъекты::Пропустить Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80d2ae53ea7732a2120cf0431f33f929a0a6bc05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716274"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Этот метод пропускает указанное количество элементов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Число пропускаемых элементов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. `S_FALSE` Возвращает, `celt` если больше, чем число оставшихся элементов; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если `celt` указывается значение, превышающее количество оставшихся элементов, перечисление устанавливается до конца и `S_FALSE` возвращается.

## <a name="see-also"></a>См. также
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
