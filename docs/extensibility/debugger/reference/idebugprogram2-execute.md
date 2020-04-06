---
title: IDebugProgram2::Выполнение Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722981"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Продолжает запуск этой программы из остановленного состояния. Любое предыдущее состояние выполнения (например, шаг) очищается, и программа снова начинает выполнение.

> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [«Выполнение».](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда пользователь начинает выполнение из остановленного состояния в потоке другой программы, этот метод вызывается в этой программе. Этот метод также вызывается, когда пользователь выбирает команду **Start** из меню **Debug** в IDE. Реализация этого метода может быть так же проста, как вызов метода [Резюме](../../../extensibility/debugger/reference/idebugthread2-resume.md) на текущем потоке в программе.

> [!WARNING]
> Не отправляйте событие остановки или немедленное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) во время обработки этого вызова; в противном случае отладчик может повесить.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugthread2-resume.md)
