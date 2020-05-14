---
title: IDebugEngineLaunch2::LaunchSuspended Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730544"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Этот метод запускает процесс с помощью отладки двигателя (DE).

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
(в) Название машины, в которой для запуска процесса. Используйте нулевую стоимость для указания локальной машины.

`pPort`\
(в) Интерфейс [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md) представляющий порт, в который будет работать программа.

`pszExe`\
(в) Название исполняемых будет запущен.

`pszArgs`\
(в) Аргументы, чтобы перейти к исполняемым. Может быть нулевая стоимость, если нет аргументов.

`pszDir`\
(в) Название рабочего каталога, используемого исполняемым. Может быть нулевая стоимость, если не требуется рабочий каталог.

`bstrEnv`\
(в) Блок среды строк NULL-terminated, за которым следует дополнительный терминатор NULL.

`pszOptions`\
(в) Варианты исполняемых.

`dwLaunchFlags`\
(в) Определяет [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) для сеанса.

`hStdInput`\
(в) Обработка альтернативного входиного потока. Может быть 0, если перенаправление не требуется.

`hStdOutput`\
(в) Обработка альтернативного потока вывода. Может быть 0, если перенаправление не требуется.

`hStdError`\
(в) Обработка альтернативного потока вывода ошибок. Может быть 0, если перенаправление не требуется.

`pCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) который получает события отладчика.

`ppDebugProcess`\
(ваут) Возвращает полученный [iDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий запущенный процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Обычно [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] запускает программу с помощью метода [LaunchSuspended,](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) а затем прикрепляет отладчикк к приостановленной программе. Однако существуют обстоятельства, при которых отладоть двигатель может потребоваться для запуска программы (например, если отладка является частью [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] переводчика, а отладка программы является интерпретируемым языком), в этом случае используется `IDebugEngineLaunch2::LaunchSuspended` метод.

 Метод [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) вызывается для запуска процесса после успешного запуска процесса в приостановленном состоянии.

## <a name="see-also"></a>См. также
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
