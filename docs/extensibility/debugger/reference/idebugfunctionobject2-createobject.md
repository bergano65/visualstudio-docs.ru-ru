---
title: 'IDebugFunctionObject2:: CreateObject | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728477"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Создает объект, использующий конструктор заданных параметров флагов оценки и значение времени ожидания.

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
окне Объект [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , представляющий конструктор создаваемого объекта.

`dwArgs`\
окне Число параметров в `pArg` массиве. Представляет число параметров, передаваемых конструктору.

`pArgs`\
окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих параметры, переданные конструктору.

`dwEvalFlags`\
окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.

`dwTimeout`\
окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте **бесконечность** для бесконечного ожидания.

`ppObject`\
заполняет Возвращает объект **идебугобжект** , представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса, или другой сложный тип, для которого требуется конструктор, который является параметром.

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
