---
title: IDebugPrimitiveTypeField::GetPrimitiveType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83412fb612976911c8e88b683a9a3953661e8507
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202793"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Извлекает тип-примитив, который связан с этим полем.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPrimitiveType (
   DWORD* pdwType
);
```

```csharp
int GetPrimitiveType (
   out uint pdwType
);
```

## <a name="parameters"></a>Параметры
`pdwType`\
[out] Значение из [перечисление CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , представляющий тип-примитив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE`.

## <a name="see-also"></a>См. также
- [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)