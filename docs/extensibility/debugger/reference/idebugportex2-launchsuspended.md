---
title: IDebugPortEx2::ЗапускПриостановлено (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725098"
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

## <a name="parameters"></a>Параметры
`pszExe`\
(в) Название исполняемых будет запущен. Это может быть полный путь или относительно рабочего каталога, указанного в параметре. `pszDir`

`pszArgs`\
(в) Аргументы, чтобы перейти к исполняемым. Может быть нулевая стоимость, если нет аргументов.

`pszDir`\
(в) Название рабочего каталога, используемого исполняемым. Может быть нулевая стоимость, если не требуется рабочий каталог.

`bstrEnv`\
(в) Блок среды нулевых строк, а затем дополнительный терминатор NULL.

`hStdInput`\
(в) Обработка альтернативного входиного потока. Может быть 0, если перенаправление не требуется.

`hStdOutput`\
(в) Обработка альтернативного потока вывода. Может быть 0, если перенаправление не требуется.

`hStdError`\
(в) Обработка альтернативного потока вывода ошибок. Может быть 0, если перенаправление не требуется.

`ppPortProcess`\
(ваут) Возвращает объект [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) представляющий запущенный процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод должен запустить процесс так, чтобы он был приостановлен и не запускал какой-либо код. Для возобновления процесса называется метод [ResumeProcess.](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)

 Программа также может быть запущена с движка отладки. Для получения [подробной](../../../extensibility/debugger/launching-a-program.md)информации см.

## <a name="see-also"></a>См. также
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Запуск программы](../../../extensibility/debugger/launching-a-program.md)
