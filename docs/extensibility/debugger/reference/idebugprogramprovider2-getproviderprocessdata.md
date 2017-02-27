---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает список выполняющихся программ из указанного процесса.  
  
## Синтаксис  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### Параметры  
 `Flags`  
 \[in\] сочетание пометит из [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) перечисление.  Следующие флаги типичны для данного вызова.  
  
|Flag|Описание|  
|----------|--------------|  
|`PFLAG_REMOTE_PORT`|Вызывающий код выполняется на удаленном компьютере.|  
|`PFLAG_DEBUGGEE`|Вызывающий объект в настоящее время отладки \(дополнительные сведения о выстраивать будет возвращена для каждого узла\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был вложен в но не был запущен отладчиком.|  
|`PFLAG_GET_PROGRAM_NODES`|Вызывающий объект запрашивает список узлов программы должен быть возвращен.|  
  
 `pPort`  
 \[in\] порт вызывающий процесс запущен.  
  
 `processId`  
 \[in\] [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура, содержащая идентификатор процесса, содержащего программу в вопросе.  
  
 `EngineFilter`  
 \[in\] массив GUID для отладки отладчиков присвоенные для отладки этот процесс \(они будут использоваться для фильтрации программы, которые фактически возвращенных в зависимости от того, предоставляемая поддержка обработчиков; если обработчики не заданы, то будут возвращены все программы\).  
  
 `pProcess`  
 \[out\] a [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структура, заполняемую с данными.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод обычно вызывается процессом, чтобы получить список программ, запущенных в этом процессе.  Возвращают сведения список IDebugProgramNode2 объекты.  
  
## См. также  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)