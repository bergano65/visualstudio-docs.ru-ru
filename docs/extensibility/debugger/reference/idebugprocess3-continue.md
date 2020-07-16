---
title: 'IDebugProcess3:: Continue | Документация Майкрософт'
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
ms.openlocfilehash: aba0863ad7c50bf5c14e7a30c06097825b8cf5ec
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386801"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Возобновляет выполнение этого процесса из остановленного состояния. Все предыдущие состояния выполнения (например, шаг) сохраняются, и процесс начинает выполняться снова.

> [!NOTE]
> Этот метод следует использовать вместо [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, который должен быть продолжен.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод вызывается для этого процесса независимо от того, сколько процессов отлаживается или какой процесс вызвал событие остановки. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто оно никогда не было остановлено до завершения предыдущего выполнения. То есть, если поток в этом процессе выполнял операцию пошагового выполнения и был остановлен из-за остановки какого-либо другого процесса, а затем `Continue` был вызван, указанный поток должен выполнить исходную операцию пошагового выполнения.

 **Предупреждение об ошибке** Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
