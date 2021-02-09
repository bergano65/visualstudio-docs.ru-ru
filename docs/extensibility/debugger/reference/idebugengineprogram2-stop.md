---
title: 'IDebugEngineProgram2:: останавливается | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6013770e3a334e7924cafe4563d437d4f7730bfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892688"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Останавливает все потоки, выполняющиеся в этой программе.

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

## <a name="remarks"></a>Remarks
 Этот метод вызывается при отладке этой программы в среде с несколькими программами. При получении события остановки от какой-либо другой программы этот метод вызывается в этой программе. Реализация этого метода должна быть асинхронной; то есть не все потоки должны быть остановлены перед возвратом этого метода. Реализация этого метода может быть такой же простой, как вызов метода [каусебреак](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) в этой программе.

 Разработчики должны отправить [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) при остановке программы.

## <a name="see-also"></a>См. также раздел
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
