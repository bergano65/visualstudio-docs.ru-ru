---
title: IDebugFunctionObject::CreateObjectNoConstructor | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e6225099b3b88cbbbb73884cbd93be4f7976e50
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200843"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Создает объект с помощью отсутствует конструктор.

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
[in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий тип создаваемого объекта.

`ppObject`\
[out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр структуры или сложного типа (который не требуется конструктор), являющийся параметром функции представленный [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.

 Если параметр объекта требуется конструктор, вызвать [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) метод.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)