---
title: IDebugEngineProgram2:WatchForThreadStep Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730353"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Часы для выполнения (или остановки просмотра для выполнения), чтобы произойти на данном потоке.

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
(в) Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий ступенчатую программу.

`dwTid`\
(в) Определяет идентификатор потока для просмотра.

`fWatch`\
(в) Ненулевой`TRUE`( ) означает начать наблюдение за `dwTid`выполнением на потоке, идентифицированном ; в противном`FALSE`случае, ноль `dwTid`() означает прекратить наблюдение за исполнением на .

`dwFrame`\
(в) Определяет индекс кадра, который управляет типом шага. Когда это значение равно нулю (0), тип шага "шаг в" и программа `dwTid` должна остановиться всякий раз, когда поток, идентифицированный выполняет. Когда `dwFrame` нет нуля, тип шага "шаг над", и программа должна остановиться только в том случае, если поток, `dwTid` `dwFrame`идентифицированный работает в кадре, индекс которого равен или выше на стеке, чем.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда диспетчер отладки сеанса (SDM) `pOriginatingProgram` наступает на программу, определенную парапараметроком, она уведомляет все другие прикрепленные программы, вызывая этот метод.

 Этот метод применим только к однонистовом уступанию.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
