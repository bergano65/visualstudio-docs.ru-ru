---
title: IDebugProgram2::Execute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29839e2f2adb4a0e560b5b58d4226fd61596128c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412846"
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