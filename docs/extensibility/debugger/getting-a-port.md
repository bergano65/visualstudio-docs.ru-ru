---
title: Получение порта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39aa81216ad3b6e98162c68136734589b008873b
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645085"
---
# <a name="get-a-port"></a>Назначить порт
Порт представляет подключение к компьютеру, на которой выполняются процессы. Машины может быть на локальном компьютере или удаленном компьютере (который может возможно использоваться операционную систему не под управлением Windows, см. в разделе [порты](../../extensibility/debugger/ports.md) Дополнительные сведения).  
  
 Представленный портом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс. Он используется для получения сведений о процессах, запущенных на компьютере, который подключен порт.  
  
 Модуль отладки требуется доступ к порту для удовлетворения запросов для сведений о процессе и регистрацию узлов программы с портом. Например, если модуль отладки реализует [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейс и реализацию для [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод могут мечтать порт обязательный процесс возвращаемые данные.  
  
 Visual Studio предоставляет необходимые портов для обработчика отладки, и он получает этот порт поставщика порта. Если программа подключен к (либо из в отладчике, либо из-за исключения исключение, которое запускает диалоговое окно Just-in-Time [JIT]), пользователю предоставляется выбор транспорта (другое название поставщика порта) для использования. В противном случае если пользователь запускает программу в отладчике, система проектов указывает поставщика порта для использования. В любом случае Visual Studio создает экземпляр поставщика порта, представленного [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейсов и запросит новый порт, вызвав [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) с [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) интерфейс. Этот порт затем передается в модуль отладки в одной форме или на другом.  
  
## <a name="example"></a>Пример  
 Этот фрагмент кода показано, как использовать порт, передаваемое [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Регистрация узла программы в [ResumeProcess для](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Параметры, не связанные непосредственно с этой концепции опущены для ясности.  
  
> [!NOTE]
>  В этом примере используется порт для запуска и возобновить процесс и предполагается, что [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) интерфейс реализуется через порт. Это отнюдь не единственный способ выполнения этих задач, и возможно, что порт может не даже будет задействована отличных от и программа [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) предоставленные ему.  
  
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
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)   
 [Порты](../../extensibility/debugger/ports.md)