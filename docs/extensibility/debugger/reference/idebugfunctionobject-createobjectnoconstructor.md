---
title: 'Идебугфунктионобжект:: Креатеобжектноконструктор | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2c47f51fb0ddc47218b11fe5673e0ede8362ff89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921077"
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
окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий тип создаваемого объекта.

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр структуры или сложного типа (который не требует конструктора), который является параметром функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Если для параметра объекта требуется конструктор, вызовите метод [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
