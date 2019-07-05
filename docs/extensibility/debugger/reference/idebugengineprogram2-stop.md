---
title: IDebugEngineProgram2::Stop | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba93c88eb3d7e996b2a5f19dda605653af090c94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345219"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Останавливает все потоки, выполняющиеся у этой программы.

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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается, когда эта программа отлаживается в среде с несколькими программы. При получении событии остановки из другой программы, этот метод вызывается для данной программы. Реализация этого метода должен быть асинхронным; то есть не все потоки должен обязательно быть остановлена перед возвратом этот метод. Реализация этого метода может быть простым вызовом [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) метод для данной программы.

 Событие отладки не отправляется в ответ на этот метод.

## <a name="see-also"></a>См. также
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)