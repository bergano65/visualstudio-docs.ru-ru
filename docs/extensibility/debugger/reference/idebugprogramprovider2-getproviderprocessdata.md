---
title: "IDebugProgramProvider2::GetProviderProcessData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e94e0606256eda3fb8cdcade90979342d078e125
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Извлекает список запуска программ из указанного процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
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
|`PFLAG_GET_PROGRAM_NODES`|Вызывающий объект запрашивает список узлов в программе должен быть возвращен.|  
  
 `pPort`  
 [in] Прослушивает порт вызывающего процесса.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, содержащую идентификатор процесса, в которой находится программа в вопросе.  
  
 `EngineFilter`  
 [in] Массив идентификаторов GUID для отладчики, назначенный для отладки этого процесса (они будут использоваться для фильтрации программы, которые фактически возвращаются на основе что поддерживать предоставленного ядер, а если обработчики не заданы, то будут возвращены все программы).  
  
 `pProcess`  
 [out] Объект [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структуру, которая содержит требуемые сведения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно вызывается процессом, чтобы получить список программ, запущенных в этом процессе. Возвращенные сведения приведен список [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объектов.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)