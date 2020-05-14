---
title: MODULE_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714258"
---
# <a name="module_flags"></a>MODULE_FLAGS
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

## <a name="fields"></a>Поля
 `MODULE_FLAG_NONE`\
 Не указывается модуль.

 `MODULE_FLAG_SYSTEM`\
 Определяет модуль системы.

 `MODULE_FLAG_SYMBOLS`\
 Определяет модуль символов.

 `MODULE_FLAG_64BIT`\
 Определяет 64-разрядный модуль.

 `MODULE_FLAG_OPTIMIZED`\
 Специфика модуль была оптимизирована. Это состояние отражается в окне **модулей.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Специфика модуля не была оптимизирована. Это состояние отражается в окне **модулей.** Это состояние по умолчанию.

## <a name="remarks"></a>Примечания
 Используется для `m_dwModuleFlags` члена [структуры MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
