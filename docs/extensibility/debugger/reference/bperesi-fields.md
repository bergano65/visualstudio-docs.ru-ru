---
title: BPERESI_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5877bc3fa7fb2844030a862a0a8f8244cffdbb6d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317553"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Указывает сведения, которые требуется получить сведения о неудачных разрешении точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>Участники
PERESI_BPRESLOCATION  
Initialize и использование `bpResLocation` (точки останова разрешения) поле [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры.

BPERESI_PROGRAM  
Инициализация и использование `pProgram` поле `BP_ERROR_RESOLUTION_INFO` структуры.

BPERESI_THREAD  
Инициализация и использование `pThread` поле `BP_ERROR_RESOLUTION_INFO` структуры.

BPERESI_MESSAGE  
Инициализация и использование `bstrMessage` поле `BP_ERROR_RESOLUTION_INFO` структуры.

BPERESI_TYPE  
Инициализация и использование `dwType` (тип точки останова) поле `BP_ERROR_RESOLUTION_INFO` структуры.

BPERESI_ALLFIELDS  
Инициализировать или использовать все поля `BP_ERROR_RESOLUTION_INFO` структуры.

## <a name="remarks"></a>Примечания
Переданный в качестве параметра для [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод, чтобы указать, какие поля [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры должны быть инициализированы.

Эти значения также используются для указания, какие поля в `BP_ERROR_RESOLUTION_INFO` структуры не используются и допустимым при возвращении этой структуре.

Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
