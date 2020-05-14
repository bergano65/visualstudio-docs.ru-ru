---
title: IDebugFunctionObject2::CreateObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728477"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Создает объект, который использует конструктор, учитывая настройки флага оценки и значение тайм-аута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Параметры
`pConstructor`\
(в) Объект [IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) представляющий конструктор создаваемого объекта.

`dwArgs`\
(в) Количество параметров в `pArg` массиве. Представляет количество параметров, переданных конструктору.

`pArgs`\
(в) Массив объектов [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий параметры, передаваемые конструктору.

`dwEvalFlags`\
(в) Комбинация флагов из перечисления [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) которые определяют, как должна выполняться оценка.

`dwTimeout`\
(в) Максимальное время, в миллисекундах, ждать, прежде чем вернуться из этого метода. Используйте **INFINITE,** чтобы ждать бесконечно.

`ppObject`\
(ваут) Возвращает **IDebugObject,** представляющий вновь созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод для создания объекта, представляющего экземпляр класса, или другой сложный тип, требующий конструктора, то есть параметра.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
