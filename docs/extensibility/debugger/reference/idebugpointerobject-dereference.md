---
title: IDebugPointerObject::Dereference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90a5a1f6fca718397654e836f41089b122425f0f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209384"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Получает объект, на который указывает.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`dwIndex`\
[in] Указывает смещение в простых байтах от начала объекта.

`ppObject`\
[out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект представляет объект, на который указывает, а также смещение, если таковые имеются.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки. Возвращает значение E_FAIL, если этот объект не указывает на другой объект.

## <a name="remarks"></a>Примечания
 Объект, на который указывает может быть примитивом или более сложного типа, например класса или структуры.

## <a name="see-also"></a>См. также
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)