---
title: "IDebugStackFrame3::InterceptCurrentException | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9631f2206705ef6daf36b355aa6cb1d5be6458d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Вызывается в отладчике на текущий кадр стека при ему нужно перехватить текущее исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFlags`  
 [in] Указывает различные действия. В настоящее время только [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) значение `IEA_INTERCEPT` поддерживается и должен быть указан.  
  
 `pqwCookie`  
 [out] Уникальное значение, определяющее конкретного исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
 Ниже приведены наиболее распространенные ошибки возвращает.  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Не может быть перехвачено текущее исключение.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Текущий кадр выполнения еще не завершен поиск обработчика еще.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Этот метод не поддерживается для этого кадра.|  
  
## <a name="remarks"></a>Примечания  
 При возникновении исключения отладчик получает управление от время выполнения в ключевых точках во время процесса обработки исключений. Во время этих ключевые моменты отладчик может потребовать от текущего кадра стека хочет перехватить исключение фрейма. Таким образом перехваченные исключения является по сути обработчика исключений на лету для кадра стека, даже если этот кадр стека не имеет обработчика исключений (например, блок try/catch в программном коде).  
  
 Когда отладчик хочет знать, должно быть перехвачено исключение, он вызывает этот метод для текущего кадра стека. Этот метод отвечает за обработку всех сведениями об исключении. Если [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) не реализован интерфейс или `InterceptStackException` метод возвращает все ошибки, то отладчик продолжает выполнение, обычно обработка исключения.  
  
> [!NOTE]
>  Исключения могут быть перехвачены только в управляемом коде, то есть отлаживаемой программы, выполняющейся в списке времени выполнения .NET. Конечно, можно реализовать языка сторонних разработчиков `InterceptStackException` в свои собственные модули отладки по усмотрению.  
  
 После завершения перехвата [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) получает сигнал.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)