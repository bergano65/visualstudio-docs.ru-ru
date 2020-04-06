---
title: IDebugПроцесс3::Продолжить Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723778"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Продолжает сябьи запустить этот процесс из остановленного состояния. Любое предыдущее состояние выполнения (например, шаг) сохраняется, и процесс снова запускается.

> [!NOTE]
> Этот метод следует использовать вместо [продолжения](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток, который будет продолжен.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается на этот процесс независимо от того, сколько процессов отлажено, или какой процесс генерируется событие остановки. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто оно никогда не прекращалось до завершения предыдущего выполнения. То есть, если поток в этом процессе выполнял операцию по переполню `Continue` и был остановлен из-за того, что какой-то другой процесс остановился, а затем был вызван, указанный поток должен завершить исходную операцию.

 **Предупреждение** Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
