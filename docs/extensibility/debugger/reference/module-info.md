---
title: MODULE_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714315"
---
# <a name="module_info"></a>MODULE_INFO
Описывает определенный модуль (DLL, EXE или сборка).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Участники
 `dwValidFields`\
 Комбинация флагов [из MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисления, которая определяет, какие поля заполнены.

 `m_bstrName`\
 Имя модуля.

 `m_bstrUrl`\
 URL-адрес модуля.

 `m_bstrVersion`\
 Модульная версия.

 `m_bstrDebugMessage`\
 Например, дополнительное сообщение о модуле "Символы не могут быть загружены".

 `m_addrLoadAddress`\
 Адрес загрузки модуля.

 `m_addrPreferredLoadAddress`\
 Предпочтительный адрес нагрузки модуля.

 `m_dwSize`\
 Размер модуля.

 `m_dwLoadOrder`\
 Заказ загрузки модуля.

 `m_TimeStamp`\
 Время последнего изменения файла символа.

 `m_bstrUrlSymbolLocation`\
 Расположение файла символа (например,\\".") указано в модуле. Используется в качестве стартового места для поиска символов для модуля.

 `m_dwModuleFlags`\
 Комбинация флагов из [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) перечисления, описывающая модуль.

## <a name="remarks"></a>Примечания
 Эта структура передается методу [GetInfo,](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) где она заполняется.

 Эта структура соответствует каждому модулю, указанному в окне **модулей.**

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
