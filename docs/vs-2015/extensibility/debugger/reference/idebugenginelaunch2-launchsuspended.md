---
title: 'IDebugEngineLaunch2:: Лаунчсуспендед | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08f59f9f099f4cec52760c8a8364feb8f5481ffa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195744"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод запускает процесс с помощью модуля отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
```csharp  
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
  
#### <a name="parameters"></a>Параметры  
 `pszMachine`  
 окне Имя компьютера, на котором запускается процесс. Используйте значение null, чтобы указать локальный компьютер.  
  
 `pPort`  
 окне Интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт, в котором будет выполняться программа.  
  
 `pszExe`  
 окне Имя исполняемого файла, который необходимо запустить.  
  
 `pszArgs`  
 окне Аргументы для передачи в исполняемый файл. Может иметь значение null, если аргументы отсутствуют.  
  
 `pszDir`  
 окне Имя рабочего каталога, используемого исполняемым файлом. Может иметь значение null, если рабочий каталог не требуется.  
  
 `bstrEnv`  
 окне Блок среды строк, заканчивающихся нулем, за которыми следует дополнительный символ NULL.  
  
 `pszOptions`  
 окне Параметры для исполняемого файла.  
  
 `dwLaunchFlags`  
 окне Указывает [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) для сеанса.  
  
 `hStdInput`  
 окне Обработчик для альтернативного входного потока. Может иметь значение 0, если перенаправление не требуется.  
  
 `hStdOutput`  
 окне Обработчик для альтернативного выходного потока. Может иметь значение 0, если перенаправление не требуется.  
  
 `hStdError`  
 окне Обработчик альтернативного выходного потока ошибок. Может иметь значение 0, если перенаправление не требуется.  
  
 `pCallback`  
 окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , который получает события отладчика.  
  
 `ppDebugProcess`  
 заполняет Возвращает результирующий объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий запущенный процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Как правило, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] запускает программу с помощью метода [лаунчсуспендед](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) , а затем присоединяет отладчик к приостановленной программе. Однако существуют обстоятельства, в которых модулю отладки может потребоваться запустить программу (например, если модуль отладки является частью интерпретатора, а отлаживаемая программа — интерпретируемый язык). в этом случае [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] используется `IDebugEngineLaunch2::LaunchSuspended` метод.  
  
 Метод [ресумепроцесс](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) вызывается для запуска процесса после того, как процесс был успешно запущен в приостановленном состоянии.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [лаунчсуспендед](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
