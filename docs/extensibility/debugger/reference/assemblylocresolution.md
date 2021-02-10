---
title: АССЕМБЛИЛОКРЕСОЛУТИОН | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2611828f1e9bb2aec740e392db18ce60839d19a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952399"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Указывает, где находится сборка.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Поля
`ALR_NAME`\
Сборка находится в текущем пространстве имен.

`ALR_USERDIR`\
Сборка находится в каталоге пользователя.

`ALR_SHAREDDIR`\
Сборка находится в общем каталоге.

`ALR_REMOTEDIR`\
Сборка находится в удаленном каталоге.

## <a name="remarks"></a>Remarks
Эти значения возвращаются методами [ресолвеассемблиреф](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) и [жетманажедвиеверкреатиондата](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) .

Эти значения можно сочетать с `OR` операцией.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
