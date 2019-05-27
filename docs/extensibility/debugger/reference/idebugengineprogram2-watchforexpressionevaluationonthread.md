---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41a644c2e0fb36cd39d55bf853f8362033eec8a0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212426"
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

## <a name="parameters"></a>Параметры
`pOriginatingProgram`\
[in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, которая оценивает выражение.

`dwTid`\
[in] Указывает идентификатор потока.

`dwEvalFlags`\
[in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, каким образом будет осуществляться вычисления.

`pExprCallback`\
[in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для отправки события отладки, возникающие во время вычисления выражения.

`fWatch`\
[in] Если ненулевое значение (`TRUE`), позволяет вычислять выражение в потоке, идентифицируемый `dwTid`; в противном случае — значение ноль (`FALSE`) запрещает вычисление выражений в этом потоке.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда диспетчер отладки сеансов (SDM) запрашивает программы, идентифицируемый `pOriginatingProgram` параметр, чтобы вычислить выражение, он уведомляет всех остальных присоединенных программ путем вызова данного метода.

 Вычисление выражений в одной программе может вызвать код в другой, из-за вычисление функции или оценки любого `IDispatch` свойства. По этой причине этот метод позволяет вычисления выражения для запуска и завершения, несмотря на то, что поток может быть остановлена в этой программе.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)