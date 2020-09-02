---
title: 'IDebugEngineProgram2:: Ватчфорекспрессионевалуатиононсреад | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431476"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Разрешает (или запрещает) вычисление выражений в заданном потоке, даже если программа остановлена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pOriginatingProgram`  
 окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, которая вычисляет выражение.  
  
 `dwTid`  
 окне Задает идентификатор потока.  
  
 `dwEvalFlags`  
 окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.  
  
 `pExprCallback`  
 окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , который будет использоваться для отправки событий отладки, происходящих во время вычисления выражения.  
  
 `fWatch`  
 окне Если ненулевое значение ( `TRUE` ), разрешает вычисление выражений в потоке, определенном `dwTid` ; в противном случае ноль ( `FALSE` ) запрещает вычисление выражений в этом потоке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если диспетчер отладки сеансов (SDM) запрашивает программу, определяемую `pOriginatingProgram` параметром, для вычисления выражения уведомляет все другие присоединенные программы, вызывая этот метод.  
  
 Вычисление выражений в одной программе может привести к тому, что код будет выполняться в другой из-за вычисления функции или оценки любых `IDispatch` свойств. Поэтому этот метод позволяет выполнять и завершать вычисление выражений, даже если поток может быть остановлен в этой программе.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [евалфлагс](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
