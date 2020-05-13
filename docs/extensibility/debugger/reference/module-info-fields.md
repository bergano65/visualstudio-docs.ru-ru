---
title: MODULE_INFO_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714319"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Осваируем флаги для информации о модуле отладки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Поля
 `MIF_NONE`\
 Инициализация/использование ни одного из полей в структуре.

 `MIF_NAME`\
 Инициализация/использование `m_bstrName` поля в [структуре MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Инициализация/использование `m_bstrUrl` `MODULE_INFO` поля в структуре.

 `MIF_VERSION`\
 Инициализация/использование `m_bstrVersion` `MODULE_INFO` поля в структуре.

 `MIF_DEBUGMESSAGE`\
 Инициализация/использование `m_bstrDebugMessage` `MODULE_INFO` поля в структуре.

 `MIF_LOADADDRESS`\
 Инициализация/использование `m_addrLoadAddress` `MODULE_INFO` поля в структуре.

 `MIF_PREFFEREDADDRESS`\
 Инициализация/использование `m_addrPreferredLoadAddress` `MODULE_INFO` поля в структуре.

 `MIF_SIZE`\
 Инициализация/использование `m_dwSize` `MODULE_INFO` поля в структуре.

 `MIF_LOADORDER`\
 Инициализация/использование `m_dwLoadOrder` `MODULE_INFO` поля в структуре.

 `MIF_TIMESTAMP`\
 Инициализация/использование `m_TimeStamp` `MODULE_INFO` поля в структуре.

 `MIF_URLSYMBOLLOCATION`\
 Инициализация/использование `m_bstrUrlSymbolLocation` `MODULE_INFO` поля в структуре.

 `MIF_FLAGS`\
 Инициализация/использование `m_dwModuleFlags` `MODULE_INFO` поля в структуре.

 `MIF_ALLFIELDS`\
 Инициализация/использование всех `MODULE_INFO` полей в структуре.

## <a name="remarks"></a>Примечания
 Эти значения передаются в качестве аргумента методу [GetInfo,](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) чтобы указать, какие поля [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры должны быть инициализированы.

 Эти значения также используются `MODULE_INFO` в структуре для указания того, какие поля используются и действительны.

 Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
