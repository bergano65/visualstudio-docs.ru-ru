---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979813"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Запускает исполняемый файл.  
  
## <a name="syntax"></a>Синтаксис  
  
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
