---
title: Регистрация Программы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713170"
---
# <a name="register-the-program"></a>Регистрация программы
После того, как отладка двигателя приобрела порт, представленный интерфейсом [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) следующим шагом в обеспечении отладки программы является регистрация его в порту. После регистрации программа доступна для отладки одним из следующих средств:

- Процесс присоединения, который позволяет отладчику получить полный контроль отладки работающего приложения.

- Отладка точного времени (JIT), которая позволяет после фактической отладки программы, которая работает независимо от отладчика. Когда архитектура времени выполнения устраняет неисправность, отладчик уведомляется перед операционной системой или средой времени выполнения, высвобождает память и ресурсы программы сбоя.

## <a name="registering-procedure"></a>Процедура регистрации

### <a name="to-register-your-program"></a>Зарегистрировать программу

1. Вызовите метод [AddProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) реализованный портом.

     `IDebugPortNotify2::AddProgramNode`требуется указатель на интерфейс [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

     Обычно, когда операционная система или среда времени выполнения загружает программу, она создает узла программы. Если отладка двигателя (DE) предлагается загрузить программу, DE создает и регистрирует узла программы.

     Ниже приводится отладка двигателя запуска программы и регистрации его в порту.

    > [!NOTE]
    > Этот пример кода не единственный способ запуска и возобновления процесса; этот код является главным примером регистрации программы в порту.

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
- [Получение порта](../../extensibility/debugger/getting-a-port.md)
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
