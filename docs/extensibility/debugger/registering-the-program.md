---
title: "Регистрация программы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "программы регистрации"
  - "отладка [пакет SDK для отладки], программы регистрации"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Регистрация программы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

После того как отладчик приобретал порт, представленный IDebugPort2 интерфейс, следующий шаг в поле разрешить программа для отладки зарегистрировать его с портом.  Как только после регистрации программа доступна для отладки означает одно из следующих значений:  
  
-   Процесс вложение, который позволяет отладчику к элементу управления отладки увеличения полного выполнения приложения.  
  
-   JIT отладка, что позволяет при отладке после \-\- фактов программы, которая работает независимо от отладчика.  Если архитектура среды выполнения перехватывает ошибку, отладчик получает уведомление до выпусков операционной системы или среды выполнения память и ресурсы ошибаясь программы.  
  
## Регистрация процедура  
  
#### Регистрация программы  
  
1.  Вызовите [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) метод, реализуемый портом.  
  
     `IDebugPortNotify2::AddProgramNode` требует указателя на  [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс.  
  
     Как правило, когда операционная система или среду выполнения загрузки программы, она создает узел программы.  Если поставлена загружает обработчик отладки \(DE\) программу, то DE создает и регистрирует узел программы.  
  
     В следующем примере показан обработчик отладки при запуске программы и при регистрации его с портом.  
  
    > [!NOTE]
    >  Это не является единственным способа запуска и продолжить процесс; это основной пример регистрация программы с портом.  
  
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
  
## См. также  
 [Приступая к порту](../../extensibility/debugger/getting-a-port.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)