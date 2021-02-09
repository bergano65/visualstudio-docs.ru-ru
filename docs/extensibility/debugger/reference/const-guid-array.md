---
title: CONST_GUID_ARRAY | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2893b6a1e977b84fba3161a33a5342f94ccc030
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900289"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
Структура, содержащая список `GUID` s.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>Члены
`dwCount`\
Число объектов `GUID` в `Members` массиве.

`Members`\
Массив объектов `GUID` s.

## <a name="remarks"></a>Remarks
Эта структура передается в метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) и возвращается из методов [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) и [ватчфорпровидеревентс](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) .

Владелец экземпляра этой структуры отвечает за освобождение выделенной памяти.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
