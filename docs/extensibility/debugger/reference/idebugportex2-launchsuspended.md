---
title: "IDebugPortEx2::LaunchSuspended | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::LaunchSuspended
helpviewer_keywords: IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a65c7a8bbf7e3ec0dba7506b435cfb39da07198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Запускает исполняемый файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>Параметры  
 `pszExe`  
 [in] Имя исполняемого файла, который будет запущен. Это может быть полный путь или относительно рабочего каталога, указанного в `pszDir` параметра.  
  
 `pszArgs`  
 [in] Аргументы, передаваемые исполняемому файлу. Может иметь значение null, если не указаны аргументы.  
  
 `pszDir`  
 [in] Имя рабочего каталога, используемого исполняемого объекта. Может иметь значение null, если нет рабочего каталога не требуется.  
  
 `bstrEnv`  
 [in] Блок среды нули, следуют дополнительные символ конца строки.  
  
 `hStdInput`  
 [in] Дескриптор дополнительного входного потока. Может быть равно 0, если перенаправление не требуется.  
  
 `hStdOutput`  
 [in] Дескриптор Альтернативный выходной поток. Может быть равно 0, если перенаправление не требуется.  
  
 `hStdError`  
 [in] Дескриптор альтернативный поток сообщений об ошибках. Может быть равно 0, если перенаправление не требуется.  
  
 `ppPortProcess`  
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий запущенного процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен быть запущен процесс, поэтому приостанавливается, чтобы он и не выполняет никакой код. [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) для возобновления процесса вызывается метод.  
  
 Также можно запустить программу из модуля отладки. Дополнительные сведения см. в разделе [запустив программу](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Запуск программы](../../../extensibility/debugger/launching-a-program.md)