---
title: 'Идебугкустоматтрибуте:: Name | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732776"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Возвращает имя настраиваемого атрибута.

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
заполняет Возвращает строку, содержащую имя пользовательского атрибута.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Имя, возвращаемое этим методом, соответствует имени класса, используемого для объявления атрибута. Это может не совпадать с именем самого класса настраиваемого атрибута, так как C# позволяет удалять суффикс "Attribute" из имени настраиваемого атрибута при его использовании в объявлении.

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
