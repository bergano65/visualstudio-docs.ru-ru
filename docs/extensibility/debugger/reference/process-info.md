---
title: PROCESS_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d35b94b6153b65672453ed8b4e7d2c0d9c2bd5eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="processinfo"></a>PROCESS_INFO
Содержит сведения о процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Участники  
 Поля  
 Сочетание флагов из [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) перечисления, укажите, какие поля заполнены.  
  
 bstrFileName  
 Полный путь имя процесса. Аналогичен вызову [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) метод с параметром `GN_FILENAME`.  
  
 bstrBaseName  
 Имя файла и расширение процесса. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_BASENAME`.  
  
 bstrTitle  
 Заголовок процесса, если он существует. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_TITLE`.  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры, определяющий процесс. Аналогичен вызову [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) метод.  
  
 dwSessionId  
 Идентификатор, на котором этот процесс выполняется в сеанс отладки.  
  
 bstrAttachedSessionName  
 Имя вложенного сеанса. Аналогичен вызову [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) метод.  
  
 CreationTime  
 Время создания процесса.  
  
 Флаги  
 Сочетание флагов из [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) перечисления, укажите свойства процесса.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)