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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ac7109b9f92a4ed7eecf57095c44fc4208b9f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891063"
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
