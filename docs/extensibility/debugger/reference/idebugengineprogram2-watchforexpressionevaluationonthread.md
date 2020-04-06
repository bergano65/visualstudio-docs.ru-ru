---
title: IdebugEngineProgram2::WatchForExpressionEvaluationOnThread Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730361"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Позволяет (или запрещает) оценку выражения происходит на данном потоке, даже если программа остановлена.

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
(в) Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий программу, которая оценивает выражение.

`dwTid`\
(в) Определяет идентификатор потока.

`dwEvalFlags`\
(в) Комбинация флагов из перечисления [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) которые определяют, как должна выполняться оценка.

`pExprCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) который будет использоваться для отправки событий отладки, которые происходят во время оценки выражения.

`fWatch`\
(в) Если не-ноль (),`TRUE`позволяет оценку `dwTid`выражения на потоке, идентифицированном ; в противном`FALSE`случае, ноль () запрещает оценку выражения на этом потоке.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда диспетчер отладки сеанса (SDM) `pOriginatingProgram` запрашивает программу, определенную параметром, для оценки выражения, он уведомляет все другие прилагаемые программы, вызывая этот метод.

 Оценка экспрессии в одной программе может привести к запуску `IDispatch` кода в другой из-за оценки функций или оценки любых свойств. Из-за этого этот метод позволяет оценивать выражения для запуска и завершения, даже если поток может быть остановлен в этой программе.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
