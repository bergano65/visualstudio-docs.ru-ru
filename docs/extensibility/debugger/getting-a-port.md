---
title: "Приступая к порту | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "порты, получение"
  - "отладка [пакет SDK для отладки], порты"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Приступая к порту
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Порт, представляющий подключение к компьютеру, на котором процессов запущены.  Этот компьютер мог быть локальным компьютером или удаленный компьютер \(который может выполнять non\-Окно\-основанная возможно, операционная система; см. [Порты](../../extensibility/debugger/ports.md) дополнительные сведения\).  
  
 Порт, представленный IDebugPort2 интерфейс.  Он используется для получения сведений о процессах, выполняющихся на компьютере подключен к порту.  
  
 Обработчик отладки требуется доступ к порту для регистрации узлы программы с портом и удовлетворить запросов для процесса сведения.  Например, если отладчик реализует [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейс, реализация  [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод может запросить требуемые сведения, возвращается порт процесса.  
  
 Visual Studio предоставляет необходимый порт в обработчик отладки, а также получают этот порт от поставщика порта.  Если вложенна программы \(или из отладчика или из\-за исключения, вызвавшего, активировать JIT \[JIT\] диалоговое окно "\), то пользователю возможность выбора транспорта \(другого имени поставщика порта\).  В противном случае если пользователь запускает программу из отладчика, то система проекта определяет поставщика порта.  В любом событии, Visual Studio создает экземпляры поставщика порта, представленный [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс и запрашивает новый порт, вызвав  [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) с  [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) интерфейс.  Этот порт затем передается в обработчик отладки в форме или другим.  
  
## Пример  
 Этот фрагмент кода показывает, как использовать порт, указанный в [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) регистрация программы внутри узла  [ResumeProcess для](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md).  Параметры не напрямую, связанные с этим понятию были пропущены для наглядности.  
  
> [!NOTE]
>  В этом примере используется порт для запуска и продолжить процесс и предполагает [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) интерфейс предоставляется через порт.  Это ни под видом единственным способом, что и для выполнения этих задач, а также возможно, что порт даже не может быть включен за исключением иметь программы IDebugProgramNode2 если на него.  
  
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
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)   
 [Порты](../../extensibility/debugger/ports.md)