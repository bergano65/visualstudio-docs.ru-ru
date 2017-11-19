---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbb3437edc8d357e6a4e96eed9bf9881970a01c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Разрешает или запрещает вычисления выражения для данного потока, даже если программа остановлена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, которая оценивает выражение.  
  
 `dwTid`  
 [in] Указывает идентификатор потока.  
  
 `dwEvalFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, как будет выполняться вычисление.  
  
 `pExprCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для отправки событий отладки, которые происходят во время вычисления выражения.  
  
 `fWatch`  
 [in] Если ненулевое значение (`TRUE`), позволяет вычисление выражений в потоке, который определяется `dwTid`; в противном случае — нуль (`FALSE`) запрещает вычисление выражений в том же потоке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда диспетчера сеанса отладки (SDM) запрашивает программы, обозначенную `pOriginatingProgram` параметр, чтобы вычислить выражение, уведомляет о всех остальных присоединенных программ путем вызова данного метода.  
  
 Вычисление выражения в одной программе может привести к коду выполняться в другой, из-за вычисление функции или оценки любого `IDispatch` свойства. По этой причине этот метод позволяет вычисления выражения для запуска и завершения, несмотря на то, что поток может быть остановлен в этой программе.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)