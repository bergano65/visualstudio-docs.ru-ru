---
title: 'IDebugProgram2:: Execute | Документация Майкрософт'
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
ms.openlocfilehash: af4650b5523595350543ac549ac162247563e418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386749"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Продолжение выполнения этой программы из остановленного состояния. Все предыдущие состояния выполнения (например, шаг) очищаются, и программа начинает выполнение повторно.

> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [EXECUTE](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .

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

## <a name="remarks"></a>Remarks
 Когда пользователь запускает выполнение из остановленного состояния в другой потоке программы, этот метод вызывается в этой программе. Этот метод также вызывается, когда пользователь выбирает команду **запуска** из меню **Отладка** в интегрированной среде разработки. Реализация этого метода может быть такой же простой, как вызов метода [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) в текущем потоке в программе.

> [!WARNING]
> Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md)
