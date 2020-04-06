---
title: IDebugEngineProgram2::Остановка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730481"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Остановка всех потоков, работающих в этой программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается при отладке этой программы в многопрограммной среде. Когда событие остановки из какой-либо другой программы получено, этот метод вызывается на эту программу. Реализация этого метода должна быть асинхронной; то есть не все потоки должны быть остановлены до возвращения этого метода. Реализация этого метода может быть так же просто, как вызов [метода CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) в этой программе.

 Исполнители должны отправить [IDebugStopCompleteEvent2,](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) когда программа останавливается.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
