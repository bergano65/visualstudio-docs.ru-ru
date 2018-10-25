---
title: IDebugPortEx2::LaunchSuspended | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a16241e406ea89b33c417bd873949979c3f6e82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882318"
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
 [in] Имя исполняемого файла для запуска. Это может быть полный путь или относительно рабочего каталога, указанного в `pszDir` параметра.  
  
 `pszArgs`  
 [in] Аргументы для передачи в исполняемый файл. Может иметь значение null, если аргументы не используются.  
  
 `pszDir`  
 [in] Имя рабочего каталога, используемого исполняемого объекта. Может иметь значение null, если нет рабочего каталога является обязательным.  
  
 `bstrEnv`  
 [in] Блок среды нулем строк, следуют дополнительные символ конца строки NULL.  
  
 `hStdInput`  
 [in] Дескриптор альтернативного входного потока. Может быть равен 0, если перенаправление не требуется.  
  
 `hStdOutput`  
 [in] Дескриптор Альтернативный выходной поток. Может быть равен 0, если перенаправление не требуется.  
  
 `hStdError`  
 [in] Обработка в поток вывода альтернативного ошибки. Может быть равен 0, если перенаправление не требуется.  
  
 `ppPortProcess`  
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) объект, представляющий запущенный процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен быть запущен процесс, поэтому он приостанавливается и не выполняет никакой код. [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) вызывается метод, чтобы возобновить процесс.  
  
 Также можно запустить программу из модуля отладки. Дополнительные сведения см. в разделе [запуск программы](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Запуск программы](../../../extensibility/debugger/launching-a-program.md)