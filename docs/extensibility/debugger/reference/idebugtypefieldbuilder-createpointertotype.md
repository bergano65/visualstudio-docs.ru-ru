---
title: IDebugTypeFieldBuilder::CreatePointerToType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e93cfc4c8a1ddb618286f79513874f8f89a9481
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199438"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Создает указатель к заданному типу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreatePointerToType(
   IDebugField*  pTypeField,
   IDebugField** pPtrToTypeField
);
```

```csharp
int CreatePointerToType(
   IDebugField     pTypeField,
   out IDebugField pPtrToTypeField
);
```

## <a name="parameters"></a>Параметры
`pTypeField`\
[in] Тип, чтобы они указывали. Он представлен [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.

`pPtrToTypeField`\
[out] Возвращает указателя, представленного новый **IDebugField** объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)