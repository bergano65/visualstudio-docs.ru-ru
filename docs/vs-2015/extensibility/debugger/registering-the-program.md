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
ms.openlocfilehash: 31d03f12a31953cbc0e20d06820dd49b5f9827e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843105"
---
# <a name="registering-the-program"></a>Регистрация программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После того как модуль отладки получит порт, представленный интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , следующий шаг при включении отладки программы заключается в его регистрации в порте. После регистрации программа доступна для отладки одним из следующих способов:  
  
- Процесс присоединения, который позволяет отладчику получить полный контроль над выполняемым приложением.  
  
- JIT-отладка, позволяющая выполнять отладку программы, работающей независимо от отладчика. Когда архитектура среды выполнения перехватывает ошибку, отладчик получает уведомления перед тем, как операционная система или среда выполнения освобождает память и ресурсы программы, вызвавшей сбой.  
  
## <a name="registering-procedure"></a>Процедура регистрации  
  
#### <a name="to-register-your-program"></a>Регистрация программы  
  
1. Вызовите метод [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) , реализованный портом.  
  
     `IDebugPortNotify2::AddProgramNode` требуется указатель на интерфейс [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
     Как правило, когда операционная система или среда выполнения загружает программу, она создает узел программы. Если модулю отладки (DE) запрашивается загрузка программы, то компонент DE создает и регистрирует узел программы.  
  
     В следующем примере показан модуль отладки, запускающий программу и регистрирующий его с помощью порта.  
  
    > [!NOTE]
    > Это не единственный способ запуска и возобновления процесса. в основном это пример регистрации программы с портом.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Получение порта](../../extensibility/debugger/getting-a-port.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
