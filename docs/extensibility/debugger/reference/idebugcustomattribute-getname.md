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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5aade49d77861d6aacdf955a167aeccbbaca4071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928436"
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
