---
title: PROCESS_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94fa9edf53d56fefb817c1a4ba6d7b3f027ab2a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886426"
---
# <a name="processinfo"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Содержит сведения о процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Сочетание флагов из [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) перечисление, указать, какие поля заполнены.  
  
 bstrFileName  
 Полное имя пути процесса. Аналогичен вызову [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) метод с параметром `GN_FILENAME`.  
  
 bstrBaseName  
 Имя файла и расширение процесса. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_BASENAME`.  
  
 bstrTitle  
 Название процесса, если он существует. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_TITLE`.  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, определяющий процесс. Аналогичен вызову [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) метод.  
  
 dwSessionId  
 Идентификатор сеанса отладки, на котором этот процесс выполняется в.  
  
 bstrAttachedSessionName  
 Имя вложенного сеанса. Аналогичен вызову [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) метод.  
  
 CreationTime  
 Время создания процесса.  
  
 Флаги  
 Сочетание флагов из [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) перечисления, укажите для свойства процесса.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

