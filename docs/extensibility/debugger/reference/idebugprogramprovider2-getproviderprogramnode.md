---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает узел программы для конкретной программы.  
  
## Синтаксис  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\] порт вызывающий процесс запущен.  
  
 `processId`  
 \[in\] [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура, содержащая идентификатор процесса, содержащего программу в вопросе.  
  
 `guidEngine`  
 \[in\] идентификатор GUID обработчика отладки, что программа вложенна \(если есть\).  
  
 `programId`  
 \[in\] идентификатор программы, для которой необходимо получить узел программы.  
  
 `ppProgramNode`  
 \[out\] IDebugProgramNode2 объект, представляющий узел программы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)