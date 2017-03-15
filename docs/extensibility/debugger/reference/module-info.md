---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "Структура MODULE_INFO"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает указанный модуль \(DLL или EXE, сборку\).  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
## Члены  
 dwValidFields  
 Комбинация из пометит [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисление, которое определяет, какие поля заполнянны.  
  
 m\_bstrName  
 Имя модуля.  
  
 m\_bstrUrl  
 URL\-адрес модуля.  
  
 m\_bstrVersion  
 Версия модуля.  
  
 m\_bstrDebugMessage  
 Дополнительное сообщение о модуле, например, "символы нельзя будет загрузить."  
  
 m\_addrLoadAddress  
 Адрес загрузки модуля.  
  
 m\_addrPreferredLoadAddress  
 Предпочтительный адрес загрузки модуля.  
  
 m\_dwSize  
 Размер модуля.  
  
 m\_dwLoadOrder  
 Порядок загрузки модуля.  
  
 m\_TimeStamp  
 Файл символов время последнего изменения.  
  
 m\_bstrUrlSymbolLocation  
 Расположение файлов символов \(например ".  \\ "\) определено в модуле.  Используется как начальное положение, чтобы найти символы для модуля.  
  
 m\_dwModuleFlags  
 Комбинация из пометит [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) перечисление, описывающее модуль.  
  
## Заметки  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, в котором он заполнен.  
  
 Эта структура соответствует каждому модулю в перечисляемый **Модули** окна.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)