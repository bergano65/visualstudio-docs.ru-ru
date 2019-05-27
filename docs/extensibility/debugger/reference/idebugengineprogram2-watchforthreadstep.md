---
title: IDebugEngineProgram2::WatchForThreadStep | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ed71649a98f86c2d75695ad02cc2aca2ea31a7b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212436"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Ожидание выполнения (или прекращает ожидать выполнения) для данного потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Параметры
`pOriginatingProgram`\
[in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программа в настоящее время шаг.

`dwTid`\
[in] Указывает идентификатор потока для отслеживания.

`fWatch`\
[in] Ненулевое значение (`TRUE`) означает, что начать просмотр для выполнения в потоке, идентифицируемый `dwTid`; в противном случае — значение ноль (`FALSE`) означает, что остановка просмотре для выполнения на `dwTid`.

`dwFrame`\
[in] Указывает индекс кадра, который определяет тип шага. Если это значение равно нулю (0), тип шага — «step into» и программа должна прекратиться, каждый раз, когда поток определяется `dwTid` выполняет. Когда `dwFrame` имеет ненулевое значение, тип шага — «step over», и программа должна прекратиться, только в том случае, если поток, указанный параметром `dwTid` выполняется в рамке, индекс которого равен или выше в стеке, чем `dwFrame`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда диспетчер отладки сеансов (SDM) действия программы, идентифицируемый `pOriginatingProgram` параметр, он уведомляет всех остальных присоединенных программ путем вызова данного метода.

 Этот метод применим только в том же потоке, пошаговое выполнение.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)