---
title: IDebugCustomAttribute::GetName Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732776"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Получает название пользовательского атрибута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Параметры
`bstrName`\
(ваут) Возвращает строку, содержащую имя пользовательского атрибута.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Имя, возвращенное этим методом, соответствует названию класса, используемого для объявления атрибута. Это может не совсем соответствовать названию самого класса пользовательских атрибутов, так как суффикс «Атрибут» может быть удален из пользовательского имени атрибута, когда он используется в декларации.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
