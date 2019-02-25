---
title: ASSEMBLYLOCRESOLUTION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06eb23c14636b72004e1089f8681adc37d68ae11
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710257"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Определяет расположение сборки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="members"></a>Участники
ALR_NAME сборка расположена в текущем пространстве имен.

ALR_USERDIR сборка расположена в каталоге пользователя.

ALR_SHAREDDIR сборка расположена в общий каталог.

ALR_REMOTEDIR сборка расположена в удаленном каталоге.

## <a name="remarks"></a>Примечания
Эти значения возвращаются [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) и [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) методы.

Эти значения могут объединяться с помощью `OR` операции.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
