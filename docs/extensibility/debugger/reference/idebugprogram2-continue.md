---
title: IDebugProgram2::Продолжить Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723073"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Продолжает запуск этой программы из остановленного состояния. Любое предыдущее состояние выполнения (например, шаг) сохраняется, и программа снова начинает исполнять.

> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [«Продолжить».](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается на эту программу независимо от того, сколько программ отлажено, или какая программа генерирует событие остановки. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто оно никогда не прекращалось до завершения предыдущего выполнения. То есть, если поток в этой программе делал пошаговую операцию и был остановлен, потому что какая-то другая программа остановилась, а затем этот метод был вызван, программа должна завершить исходную операцию.

> [!WARNING]
> Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
