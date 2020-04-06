---
title: IDebugProcess3::Выполнение Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723679"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Продолжает сябьи запустить этот процесс из остановленного состояния. Любое предыдущее состояние выполнения (например, шаг) очищается, и процесс снова запускается.

> [!NOTE]
> Этот метод следует использовать вместо [выполнения](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`\
(в) Объект [IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) представляющий поток для выполнения.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда пользователь запускает выполнение из остановленного состояния в потоке другого процесса, этот метод вызывается на этот процесс. Этот метод также вызывается, когда пользователь выбирает команду **Start** из меню **Debug** в IDE. Реализация этого метода может быть так же проста, как вызов метода [Резюме](../../../extensibility/debugger/reference/idebugthread2-resume.md) на текущем потоке в процессе.

> [!WARNING]
> Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
