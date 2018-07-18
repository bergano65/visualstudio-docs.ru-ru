---
title: MODULE_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e28756873339d504efba417d9e2fe2cc00000b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126720"
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
 dwValidFields  
 Сочетание флагов из [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисления, которое указывает, какие поля заполнены.  
  
 m_bstrName  
 Имя модуля.  
  
 m_bstrUrl  
 URL-адрес модуля.  
  
 m_bstrVersion  
 Версия модуля.  
  
 m_bstrDebugMessage  
 Дополнительное сообщение о модуле, например, «невозможно загрузить символы.»  
  
 m_addrLoadAddress  
 Адрес загрузки модуля.  
  
 m_addrPreferredLoadAddress  
 Предпочтительный адрес загрузки модуля.  
  
 m_dwSize  
 Размер модуля.  
  
 m_dwLoadOrder  
 Порядок загрузки модуля.  
  
 m_TimeStamp  
 Время последнего изменения файла символов.  
  
 m_bstrUrlSymbolLocation  
 Расположение файла символов (например, «.\\«) указан в модуле. Используется как начальное положение для найти символы для модуля.  
  
 m_dwModuleFlags  
 Сочетание флагов из [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) перечисление, описывающее модуля.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, где он заполняется.  
  
 Эта структура соответствует каждого модуля, перечисленные в **модули** окна.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)