---
title: MODULE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3a11e368b6260d00f3f6ed0b19d94aa26bd31a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683614"
---
# <a name="moduleinfo"></a>MODULE_INFO
Описание определенного модуля (DLL, EXE-файла или сборки).

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
 dwValidFields объект сочетание флагов из [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисление, указывающее, какие поля заполнены.

 m_bstrName имя модуля.

 m_bstrUrl URL-адрес модуля.

 m_bstrVersion версии модуля.

 m_bstrDebugMessage необязательное сообщение о модуле, например, «не удается загрузить символы.»

 m_addrLoadAddress адрес загрузки модуля.

 m_addrPreferredLoadAddress предпочтительный адрес загрузки модуля.

 m_dwSize размер модуля.

 m_dwLoadOrder порядок загрузки модуля.

 m_TimeStamp время последнего изменения файла символов.

 m_bstrUrlSymbolLocation расположение файла символов (например, «.\\«) указан в модуле. Использовать как начальную точку для найти символы для модуля.

 m_dwModuleFlags объект сочетание флагов из [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) перечисление, описывающее модуля.

## <a name="remarks"></a>Примечания
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, где он заполняется.

 Эта структура соответствует каждого модуля, перечисленные в **модули** окна.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)