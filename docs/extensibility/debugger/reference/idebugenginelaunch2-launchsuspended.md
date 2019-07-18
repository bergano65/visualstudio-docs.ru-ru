---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cef6382009d8139b8c166ce6b75a692e8e309557
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337184"
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

## <a name="parameters"></a>Параметры
`pszMachine`\
[in] Имя компьютера, в котором для запуска процесса. Используйте значение null, чтобы указать локальный компьютер.

`pPort`\
[in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс, представляющий порт, который программа будет запускаться в.

`pszExe`\
[in] Имя исполняемого файла для запуска.

`pszArgs`\
[in] Аргументы для передачи в исполняемый файл. Может иметь значение null, если аргументы не используются.

`pszDir`\
[in] Имя рабочего каталога, используемого исполняемого объекта. Может иметь значение null, если нет рабочего каталога является обязательным.

`bstrEnv`\
[in] Блок среды нулем строк, следуют дополнительные символ конца строки NULL.

`pszOptions`\
[in] Параметры для исполняемого файла.

`dwLaunchFlags`\
[in] Указывает [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) для сеанса.

`hStdInput`\
[in] Дескриптор альтернативного входного потока. Может быть равен 0, если перенаправление не требуется.

`hStdOutput`\
[in] Дескриптор Альтернативный выходной поток. Может быть равен 0, если перенаправление не требуется.

`hStdError`\
[in] Обработка в поток вывода альтернативного ошибки. Может быть равен 0, если перенаправление не требуется.

`pCallback`\
[in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, получающий события отладчика.

`ppDebugProcess`\
[out] Возвращает результат в виде [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий запущенный процесс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Как правило [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] запускает программу с помощью команды [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) метода и затем Присоединяет отладчик к приостановленные программы. Тем не менее, существуют обстоятельства, в которых отладчик может потребоваться для запуска программы (например, если модуль отладки является частью интерпретатор и отлаживаемой программы — это Интерпретируемый язык), в этом случае [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] использует `IDebugEngineLaunch2::LaunchSuspended` метод .

 [ResumeProcess для](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) метод вызывается для запуска процесса после процесса успешно запущена в приостановленном состоянии.

## <a name="see-also"></a>См. также
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)