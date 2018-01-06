---
title: "IDebugProgramProvider2::GetProviderProgramNode | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords: IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 150b2bc744329078319a3bf5d36dc0a97201c0c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Возвращает узел программы для конкретной программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `Flags`  
 [in] Сочетание флагов из [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) перечисления. Для этого вызова типичны следующие флаги:  
  
|Flag|Описание:|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Вызывающий объект выполняется на удаленном компьютере.|  
|`PFLAG_DEBUGGEE`|Вызывающий объект находится в состоянии отладки (Дополнительные сведения о маршалинг будут возвращены для каждого узла).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был присоединен к, но не запускается в отладчике.|  
  
 `pPort`  
 [in] Прослушивает порт вызывающего процесса.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, содержащую идентификатор процесса, в которой находится программа в вопросе.  
  
 `guidEngine`  
 [in] Идентификатор GUID отладчик, исполняемой программы (если таковые имеются).  
  
 `programId`  
 [in] Идентификатор программы, для которого нужно получить узел программы.  
  
 `ppProgramNode`  
 [out] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объект, представляющий узел Запрошенная программа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)