---
title: Получение порта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738629"
---
# <a name="get-a-port"></a>Получить порт
Порт представляет собой подключение к машине, на которой работают процессы. Эта машина может быть локальной машиной или удаленной машиной (которая, возможно, работает на основе Windows операционной системы; [см. Порты](../../extensibility/debugger/ports.md) для получения дополнительной информации).

Порт представлен интерфейсом [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md) Он используется для получения информации о процессах, работающих на машине, к ней подключен порт.

Отладочная движок нуждается в доступе к порту для регистрации узлов программы в порту и удовлетворения запросов на информацию о процессе. Например, если отладка двигателя реализует интерфейс [IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) реализация для метода [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) может запросить порт для получения необходимой информации о процессе.

Visual Studio поставляет необходимый порт для двигателя отладки, и она получает этот порт от поставщика порта. Если к программе прилагается (либо изнутри отладчика, либо из-за исключения, которое запускает поле диалога "JIT") как раз в времени), пользователю предоставляется выбор транспорта (другое название поставщика порта) для использования. В противном случае, если пользователь запускает программу из нутриундера, проектная система определяет поставщика порта для использования. В любом случае Visual Studio мгновенно вызывает у поставщика порта, представленного интерфейсом [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) и просит новый порт, позвонив в [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) с интерфейсом [IDebugPortRequest2.](../../extensibility/debugger/reference/idebugportrequest2.md) Этот порт затем передается на отладку двигателя в той или иной форме.

## <a name="example"></a>Пример
Этот фрагмент кода показывает, как использовать порт, поставляемый [launchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) для регистрации узла программы в [ResumeProcess.](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) Параметры, не имеющие прямого отношения к этой концепции, были опущены для ясности.

> [!NOTE]
> Этот пример использует порт для запуска и возобновления процесса и предполагает, что интерфейс [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) реализован в порту. Это далеко не единственный способ выполнения этих задач, и вполне возможно, что порт может даже не быть вовлечен, кроме как иметь [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) программы, данное ему.

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>См. также
- [Регистрация программы](../../extensibility/debugger/registering-the-program.md)
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
- [Порты](../../extensibility/debugger/ports.md)
