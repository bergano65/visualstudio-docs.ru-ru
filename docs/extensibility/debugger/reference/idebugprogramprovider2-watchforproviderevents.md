---
title: IDebugProgramProvider2::WatchForProviderEvents | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
helpviewer_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1dd2dcaa930db97ee8bab9b2bba168c80444dda8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121902"
---
# <a name="idebugprogramprovider2watchforproviderevents"></a>IDebugProgramProvider2::WatchForProviderEvents
Позволяет получать уведомления о событиях порт процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT WatchForProviderEvents(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   CONST_GUID_ARRAY     EngineFilter,  
   REFGUID              guidLaunchingEngine,  
   IDebugPortNotify2*   pEventCallback  
);  
```  
  
```csharp  
int WatchForProviderEvents(  
   enum_PROVIDER_FLAGS   Flags,  
   IDebugDefaultPort2    pPort,  
   AD_PROCESS_ID         ProcessId,  
   CONST_GUID_ARRAY      EngineFilter,  
   ref Guid              guidLaunchingEngine,  
   IDebugPortNotify2     pEventCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `Flags`  
 [in] Сочетание флагов из [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) перечисления. Для этого вызова типичны следующие флаги:  
  
|Flag|Описание|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Вызывающий объект выполняется на удаленном компьютере.|  
|`PFLAG_DEBUGGEE`|Вызывающий объект находится в состоянии отладки (Дополнительные сведения о маршалинг возвращается для каждого узла).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был присоединен к, но не запускается в отладчике.|  
|`PFLAG_REASON_WATCH`|Вызывающий объект должен отслеживаться события. Если этот флаг не установлен. затем удаляется событие обратного вызова и вызывающий объект больше не будет получать уведомления.|  
  
 `pPort`  
 [in] Прослушивает порт вызывающего процесса.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, содержащую идентификатор процесса, в которой находится программа в вопросе.  
  
 `EngineFilter`  
 [in] Массив идентификаторов GUID для отладчики, связанных с процессом.  
  
 `guidLaunchingEngine`  
 [in] Идентификатор GUID отладчик, запуск этого процесса (если таковые имеются).  
  
 `pEventCallback`  
 [in] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) объект, получающий уведомления о событиях.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда вызывающий объект хочет удалить обработчик событий, которое было установлено с предыдущим вызовом этого метода, вызывающий объект передает те же параметры, как это было в первый раз, но оставляет `PFLAG_REASON_WATCH` флаг.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugEngine** объекта, который предоставляет [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейса.  
  
```cpp  
STDMETHODIMP CDebugEngine::WatchForProviderEvents(  
    PROVIDER_FLAGS Flags,   
    IDebugDefaultPort2 *pPort,   
    AD_PROCESS_ID processId,   
    CONST_GUID_ARRAY EngineFilter,   
    REFGUID guidLaunchingEngine,   
    IDebugPortNotify2 *pPortNotify)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))  
    {  
        // We will only watch/send events about the process if the debugger  
        // is actually debugging the process, and only if this is an attach or a LoRIE launch  
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&  
            guidLaunchingEngine == GUID_NULL &&  
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)  
        {  
            // We don't support WatchForProviderEvents when in interop mode  
            if (m_fInterop)  
            {  
                ASSERT(!"Shouldn't ever be called in interop mode");  
                hRes = E_FAIL;  
            }  
            else  
            {  
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))  
                {  
                    // QI to get IDebugEventCallback2 which is required.  
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);  
  
                    ASSERT(pCallback != NULL);  
                    if ( pCallback != NULL )  
                    {  
                        // Register the callback  
                        hRes = this->InitDebugSession(pCallback);  
  
                        if ( S_OK == hRes )  
                        {  
                            // Get the IDebugProcess2 from the port and call AttachImpl  
                            CComPtr<IDebugProcess2> spProcess;  
  
                            hRes = pPort->GetProcess(processId, &spProcess);  
  
                            if (HREVAL(S_OK, hRes))  
                            {  
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);  
  
                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )  
                                    this->Cleanup();  
                            }  
                        }  
                        else  
                            this->Cleanup();  
                    }  
                    else  
                        hRes = E_FAIL;  
                }  
                else  
                {  
                    // Detach will be done by SDM calling on programs directly if there are managed programs.  
  
                    // This handling is the case where no managed code ever ran.  
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )  
                    {  
                        ProgramList *pProgList = this->GetProgramListCopy();  
  
                        if ( EVAL(pProgList) )  
                        {  
                            if ( pProgList->GetCount() == 0)  
                            {  
                                CComPtr<ICorDebugProcess> pCorProcess;  
  
                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);  
  
                                if (HREVAL(S_OK, hRes) )  
                                {  
                                    hRes = pCorProcess->Stop(INFINITE);  
  
                                    if ( HREVAL(S_OK, hRes) )  
                                        hRes = pCorProcess->Detach();  
                                }  
  
                                // Tell the engine that it should unregister this process from com+  
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);  
  
                                // If there are no more pids left then cleanup everything.  
                                if ( 0 == m_pPidList->GetCount() )  
                                    this->Cleanup();  
                            }  
                            // This is needed for cases where the SDM has not yet recieved program create  
                            // by the time that we need to detach (example: the managed attach succeeds,  
                            // but some other attach step fails).  
                            else  
                            {  
                                PROGNODE *pProgNode = NULL;  
                                while ( pProgNode = pProgList->Next(pProgNode) )  
                                {  
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);  
                                    hRes = pProgram->Detach();  
                                }  
                            }  
  
                            delete pProgList;  
                        }  
                    }  
                    else  
                        hRes = S_OK;  
                }  
            }  
        }  
        else  
        {  
            hRes = S_FALSE;  
        }  
    }  
    else  
    {  
        hRes = E_INVALIDARG;  
    }  
  
    return hRes;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)