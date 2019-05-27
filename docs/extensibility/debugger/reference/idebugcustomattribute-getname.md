---
title: IDebugCustomAttribute::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2556a424e5109e75b667e9f32ecac5cc26ca781b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205340"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Получает имя настраиваемого атрибута.

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
[out] Возвращает строку, содержащую имя настраиваемого атрибута.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Именованный возвращаемого этим методом соответствует имени класса, используемого для объявления атрибута. Это может не совсем соответствовать имя самого класса настраиваемого атрибута как C# позволяет суффикс «Attribute» будет удален из имени настраиваемого атрибута, при использовании в объявлении.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)