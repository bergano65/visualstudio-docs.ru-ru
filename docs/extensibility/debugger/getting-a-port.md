---
title: "Приступая к порту | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f6065c91845df020325e279a1fa3858a4f75505
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="getting-a-port"></a>Приступая к порту
Порт представляет соединение с компьютера, на котором выполняются процессы. Этого компьютера может быть на локальном компьютере или удаленном компьютере (который удалось возможно под управлением ОС, отличных от Windows операционной системой; см. [порты](../../extensibility/debugger/ports.md) для получения дополнительной информации).  
  
 Порт представляется [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейса. Он используется для получения сведений о процессах, запущенных на компьютере, которым порт подключен.  
  
 Модуль отладки требуется доступ к порту для удовлетворения запросов для сведений о процессе и регистрации программы узлов с портом. Например, если модуль отладки реализует [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейса реализации [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод попросить порт для необходимых процессов возвращаемых данных.  
  
 Visual Studio предоставляет необходимые порт модуль отладки, а этот порт будет получен от поставщика, порт. Если исполняемой программы (либо из в отладчике, либо из-за исключения было создано, которое запускает диалоговое окно только по требованию [JIT]), пользователю предоставляется выбор транспорта (другое название поставщика порта) для использования. В противном случае если пользователь запускает программу в отладчике, система проекта определяет поставщика порта для использования. В любом случае Visual Studio создает экземпляр поставщика порта, представленного [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс и запрашивает новый порт путем вызова [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) с [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) интерфейса. Этот порт, затем передается модуль отладки в одной форме или другим.  
  
## <a name="example"></a>Пример  
 Этот фрагмент кода показывает, как использовать порт, указанный для [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) регистрация в программе узла [ResumeProcess для](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Параметры, не связанные непосредственно с этой концепции опущены для ясности.  
  
> [!NOTE]
>  В этом примере используется порт для запуска и возобновить процесс и предполагается, что [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) интерфейс реализован для порта. Это ни в коем случае единственным способом выполнения этих задач, и возможно, что порт может не даже будет задействована отличный от и программа [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) заданному для него.  
  
```cpp  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)   
 [Порты](../../extensibility/debugger/ports.md)