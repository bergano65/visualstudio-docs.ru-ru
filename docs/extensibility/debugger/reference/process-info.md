---
title: "PROCESS_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5d217a411e11ee0b2b5e372634be69bf9b84ac8b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

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
  
## <a name="members"></a>Члены  
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
