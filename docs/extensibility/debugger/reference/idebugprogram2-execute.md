---
title: IDebugProgram2::Execute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27730528b552e4a545725a7a7463475be6038bba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329810"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Продолжает выполнение программы в остановленном состоянии. Очистить все предыдущие состояния выполнения (например, шаг), и начнется снова выполнение программы.

> [!NOTE]
> Этот метод является нерекомендуемым. Используйте [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) метод вместо этого.

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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда пользователь начинает выполнение в остановленном состоянии в поток некоторые другие программы, этот метод вызывается для данной программы. Этот метод также вызывается, когда пользователь выбирает **запустить** команду **Отладка** меню в интегрированной среде разработки. Реализация этого метода может быть простым вызовом [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) метода в текущем потоке в программе.

> [!WARNING]
> В случае остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)