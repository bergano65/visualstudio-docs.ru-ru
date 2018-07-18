---
title: IDebugEngineLaunch2::LaunchSuspended | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a05e8f034ec30f0f387675759cb7601f7b3fc3e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114629"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Этот метод запускает процесс с помощью модуля отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [in] Имя компьютера, в котором для запуска процесса. Используйте значение null, чтобы указать локальный компьютер.  
  
 `pPort`  
 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) порт, который программа будет запускаться в интерфейс.  
  
 `pszExe`  
 [in] Имя исполняемого файла, который будет запущен.  
  
 `pszArgs`  
 [in] Аргументы, передаваемые исполняемому файлу. Может иметь значение null, если не указаны аргументы.  
  
 `pszDir`  
 [in] Имя рабочего каталога, используемого исполняемого объекта. Может иметь значение null, если нет рабочего каталога не требуется.  
  
 `bstrEnv`  
 [in] Блок среды нули, следуют дополнительные символ конца строки.  
  
 `pszOptions`  
 [in] Параметры для исполняемого файла.  
  
 `dwLaunchFlags`  
 [in] Указывает [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) для сеанса.  
  
 `hStdInput`  
 [in] Дескриптор дополнительного входного потока. Может быть равно 0, если перенаправление не требуется.  
  
 `hStdOutput`  
 [in] Дескриптор Альтернативный выходной поток. Может быть равно 0, если перенаправление не требуется.  
  
 `hStdError`  
 [in] Дескриптор альтернативный поток сообщений об ошибках. Может быть равно 0, если перенаправление не требуется.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, получающий события отладчика.  
  
 `ppDebugProcess`  
 [out] Возвращает итоговый [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий запущенного процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] запуск программы с помощью [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) метода и затем Присоединяет отладчик к программе приостановленной. Однако существуют обстоятельства, в которых отладчик может потребоваться запустить программу (например, если отладчик входит интерпретатор и отлаживаемой программы Интерпретируемый язык), в этом случае [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] использует `IDebugEngineLaunch2::LaunchSuspended` метод .  
  
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) метод вызывается для запуска процесса после процесса успешно запущено в приостановленном состоянии.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)