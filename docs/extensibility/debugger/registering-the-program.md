---
title: Регистрация программы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: febc798888cc046e514db4013edb077e25f5aaca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="registering-the-program"></a>Регистрация программы
После отладчик получил через порт, представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс, следующий шаг в обеспечении отлаживаемой программы — для его регистрации с портом. После регистрации программа доступна для отладки одним из следующих способов:  
  
-   Процесс для присоединения, который позволяет отладчику получить полный контроль отладки запущенного приложения.  
  
-   Just-in-time (JIT) отладки, позволяющий after фактов отладки программы, которая выполняется независимо от отладчика. При архитектура выполнения перехватывает ошибку, отладчик получает уведомление до операционной системы или среды выполнения освобождает память и ресурсы сбоя программы.  
  
## <a name="registering-procedure"></a>Процедура регистрации  
  
#### <a name="to-register-your-program"></a>Чтобы зарегистрировать программу  
  
1.  Вызовите [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) метод, реализованный порт.  
  
     `IDebugPortNotify2::AddProgramNode` необходимо передать указатель на [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейса.  
  
     Как правило при загрузке программы операционной системы или среды выполнения создает узел программы. Если модуль отладки (DE) будет предложено загрузить программу DE создает и регистрирует узел программы.  
  
     В следующем примере показано отладчик, запустив программу и зарегистрировав его с портом.  
  
    > [!NOTE]
    >  Это не единственный способ запуска и возобновления процесса; Это главным образом пример регистрации программы с портом.  
  
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
 [Приступая к порту](../../extensibility/debugger/getting-a-port.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)