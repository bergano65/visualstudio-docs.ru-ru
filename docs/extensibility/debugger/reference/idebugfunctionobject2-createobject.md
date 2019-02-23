---
title: IDebugFunctionObject2::CreateObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7004e57aaf659b90b5323105c6d2c2b80baa4d0f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723127"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Создает объект, который использует конструктор параметров флаг вычисления и значение времени ожидания.

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

#### <a name="parameters"></a>Параметры
 `pConstructor`

 [in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , представляющий конструктор объекта должен быть создан.

 `dwArgs`

 [in] Число параметров в `pArg` массива. Представляет число параметров, переданных конструктору.

 `pArgs`

 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, которые представляют параметры передается конструктору.

 `dwEvalFlags`

 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, каким образом будет осуществляться вычисления.

 `dwTimeout`

 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте **БЕСКОНЕЧНЫЙ** для неограниченного времени ожидания.

 `ppObject`

 [out] Возвращает **IDebugObject** представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса или других сложный тип, который требуется конструктор, который является параметром.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)