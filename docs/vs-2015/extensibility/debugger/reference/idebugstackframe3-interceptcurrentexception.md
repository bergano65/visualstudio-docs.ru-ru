---
title: IDebugStackFrame3::InterceptCurrentException | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0dde6935a343d7ba915bd7d3954c4462056be851
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781651"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Вызывается отладчиком на текущий кадр стека, если ему необходимо перехватить текущее исключение.  
  
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
 [out] Уникальное значение, идентифицирующее конкретного исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
 Ниже приведены наиболее распространенные возвращает ошибку.  
  
|Error|Описание:|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Не может перехватить текущее исключение.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Текущий кадр выполнения еще не завершен поиск обработчика еще.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Этот метод не поддерживается для этого кадра.|  
  
## <a name="remarks"></a>Примечания  
 При возникновении исключения отладчик получает управление от время выполнения в ключевых точках во время процесса обработки исключений. Во время этих ключевых моментов отладчик может запрашивать у текущего кадра стека хочет ли кадр перехватить исключение. Таким образом перехваченные исключения является по сути обработчик исключений в режиме реального времени для кадра стека, даже если этому кадру стека не содержит обработчик исключений (например, блок try/catch в программном коде).  
  
 Когда отладчик хочет знать, если исключение должно быть перехвачены, он вызывает этот метод для текущего кадра стека. Этот метод отвечает за обработку всех сведений о исключении. Если [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) не реализован интерфейс или `InterceptStackException` метод возвращает все ошибки, а затем отладчик продолжает обработку исключения обычно.  
  
> [!NOTE]
>  Исключения могут быть перехвачены только в управляемом коде, то есть если отлаживаемая программа выполняется под .NET, время выполнения. Конечно, можно реализовать сторонние языков `InterceptStackException` в свои собственные модули отладки по усмотрению.  
  
 После завершения перехвата [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) переводится в сигнальное состояние.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

