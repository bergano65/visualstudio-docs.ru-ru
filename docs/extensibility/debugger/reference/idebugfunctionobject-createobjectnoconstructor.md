---
title: IDebugFunctionObject::CreateObjectNoConstructor (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728577"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Создает объект без конструктора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pClassObject`\
(в) Объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий тип создаваемого объекта.

`ppObject`\
(ваут) Возвращает [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий вновь созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод для создания объекта, представляющего экземпляр структуры или сложного типа (не требующего конструктора), который является параметром для функции, представленной интерфейсом [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Если параметр объекта требует конструктора, вызовите метод [CreateObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
