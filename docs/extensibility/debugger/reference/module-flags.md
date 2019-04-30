---
title: MODULE_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3ec96c5ba806e6eff735edc8093868b19ebaf5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913839"
---
# <a name="moduleflags"></a>MODULE_FLAGS
Используется для описания модуля.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="members"></a>Участники
 MODULE_FLAG_NONE указывает нет модулей.

 MODULE_FLAG_SYSTEM указывает системном модуле.

 MODULE_FLAG_SYMBOLS указан модуль символ.

 MODULE_FLAG_64BIT задает 64-разрядного модуля.

 MODULE_FLAG_OPTIMIZED указывает, модуль был оптимизирован. Это состояние отражается в **модули** окна.

 MODULE_FLAG_UNOPTIMIZED указывает, модуль не был оптимизирован. Это состояние отражается в **модули** окна. Это состояние по умолчанию.

## <a name="remarks"></a>Примечания
 Используется для `m_dwModuleFlags` членом [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.

 Эти флаги могут быть объединены с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)