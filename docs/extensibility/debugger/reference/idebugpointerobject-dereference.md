---
title: IDebugPointerObject::Dссылка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725575"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Получает объект указал.

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
(в) Простое смещение байта от начала объекта указал на.

`ppObject`\
(ваут) Возвращает объект [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий указанный объект, плюс смещение, если таковой имеется.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот объект не указывает на другой объект.

## <a name="remarks"></a>Примечания
 Указанный объект может быть примитивным или более сложным типом, например классом или структурой.

## <a name="see-also"></a>См. также
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
