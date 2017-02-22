---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Запустит исполняемый файл.  
  
## Синтаксис  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### Параметры  
 `pszExe`  
 \[in\] имя исполняемого файла для запуска.  Это может быть полный путь или по отношению к рабочей папке, указанной в `pszDir` параметр.  
  
 `pszArgs`  
 \[in\] аргументы для передачи в исполняемый файл.  Может иметь значение NULL, если аргументов.  
  
 `pszDir`  
 \[in\] имя рабочей папки, используемой исполняемым файлом.  Может иметь значение NULL, если ни одна рабочая папка не требуется.  
  
 `bstrEnv`  
 \[in\] фрагмент среды null\-завершенных строк, следуйте дополнительным терминатором NULL.  
  
 `hStdInput`  
 \[in\] дескриптор другой входной поток.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `hStdOutput`  
 \[in\] дескриптор другой поток вывода.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `hStdError`  
 \[in\] дескриптор другой поток вывода ошибок.  Может принимать значение 0, если перенаправление является обязательным.  
  
 `ppPortProcess`  
 \[out\] возвращает IDebugProcess2 объект, представляющий запущен процесс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод должен запускаться процесс таким образом, чтобы он будет приостановлен и не выполняется никакой код.  [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) метод вызывается, чтобы продолжить процесс.  
  
 Программу можно запустить из обработчика отладки.  Дополнительные сведения см. в разделе [Запуск программы](../../../extensibility/debugger/launching-a-program.md).  
  
## См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Запуск программы](../../../extensibility/debugger/launching-a-program.md)