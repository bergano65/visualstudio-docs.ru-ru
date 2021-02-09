---
title: 'Идебугженерикфиелддефинитион:: Конструктинстантиатион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ab91340c0f9baf9a75e6e283d3c1158bdbea3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911109"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Конструирует экземпляр поля по заданному массиву аргументов типа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Параметры
`cArgs`\
окне Число аргументов в `ppArgs` массиве.

`ppArgs`\
окне Массив, содержащий аргументы типа. Аргументы типа должны быть закрытыми типами (не универсальными или полностью созданными универсальными классами).

`ppConstructedField`\
заполняет Возвращает интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий новое поле.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Ограничения не проверяются.

## <a name="see-also"></a>См. также раздел
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
