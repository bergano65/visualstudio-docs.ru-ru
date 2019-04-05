---
title: Регистрация программы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4a8de9f93a04fb062954703a1c14b4c4447308
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990496"
---
# <a name="registering-the-program"></a>Регистрация программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После модуля отладки приобрела порт, представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс, следующим шагом Включение программы для отладки — для его регистрации в порт. После регистрации, эта программа доступна для отладки, одно из следующих способов:  
  
-   Процесс присоединения, который позволяет отладчику получить полное управление отладки запущенного приложения.  
  
-   Just-in-time (JIT) отладки, позволяющий after фактов отладки программы, которая выполняется независимо от отладчика. При архитектура среды выполнения перехватывает ошибку, отладчик уведомляется перед операционной системы или среды выполнения освобождает память и ресурсы программу виновный.  
  
## <a name="registering-procedure"></a>Процедура регистрации  
  
#### <a name="to-register-your-program"></a>Для регистрации программы  
  
1.  Вызовите [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) метод, реализованный порт.  
  
     `IDebugPortNotify2::AddProgramNode` требуется указатель на [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс.  
  
     Как правило при загрузке программы операционной системы или среды выполнения создает узел программы. Если подсистема отладки (DE) будет предложено загрузить программу DE создает и регистрирует узел программы.  
  
     Пример обработчика отладки, запуска программы и зарегистрировав его с портом.  
  
    > [!NOTE]
    >  Это не единственный способ запуска и возобновления процесса; Это главным образом пример регистрации программы с портом.  
  
    ```cpp#  
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
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
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
 [Получение порта](../../extensibility/debugger/getting-a-port.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
