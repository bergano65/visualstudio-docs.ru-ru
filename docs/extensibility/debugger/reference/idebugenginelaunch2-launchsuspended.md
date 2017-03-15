---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод запускает процесс с помощью обработчика отладки \(DE\).  
  
## Синтаксис  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```c#  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### Параметры  
 `pszMachine`  
 \[in\] имя компьютера, на котором для запуска процесса.  Используйте значение NULL для указания локального компьютера.  
  
 `pPort`  
 \[in\] IDebugPort2 интерфейс, представляющий порт котором программа выполняется.  
  
 `pszExe`  
 \[in\] имя исполняемого файла для запуска.  
  
 `pszArgs`  
 \[in\] аргументы для передачи в исполняемый файл.  Может иметь значение NULL, если аргументов.  
  
 `pszDir`  
 \[in\] имя рабочей папки, используемой исполняемым файлом.  Может иметь значение NULL, если ни одна рабочая папка не требуется.  
  
 `bstrEnv`  
 \[in\] фрагмент среды Null\-завершенных строк, следуйте дополнительным терминатором NULL.  
  
 `pszOptions`  
 \[in\] параметры для исполняемого файла.  
  
 `dwLaunchFlags`  
 \[in\] идентифицирует [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) для сеанса.  
  
 `hStdInput`  
 \[in\] дескриптор другой входной поток.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `hStdOutput`  
 \[in\] дескриптор другой поток вывода.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `hStdError`  
 \[in\] дескриптор другой поток вывода ошибок.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `pCallback`  
 \[in\] IDebugEventCallback2 объект, получающий события отладчика.  
  
 `ppDebugProcess`  
 \[out\] возвращает привести к IDebugProcess2 объект, представляющий запущен процесс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Обычно [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] запускает программу использование  [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) метод и затем вложение отладчика к приостановленной программе.  Однако ситуации, в которых отладчик может запустить программу \(например, если обработчик отладки, то частью отлаживаемого преобразователя и программы интерпретированный язык\), в которой регистр [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] использует  `IDebugEngineLaunch2::LaunchSuspended` метод.  
  
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) метод вызывается, чтобы начать процесс после завершения процесса был успешно запущен в состоянии приостановки.  
  
## См. также  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)