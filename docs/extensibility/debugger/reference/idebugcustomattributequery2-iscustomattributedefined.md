---
title: IDebugCustomАтрибут-Куири2::IsCustomАтрибутОпределяето (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7be649a5d65f88d8263bbe8950fda1a157855ed2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732531"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Определяет, существует ли пользовательский атрибут по имени.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Параметры
`pszCustomAttributeName`\
(в) Строка, содержащая имя пользовательского атрибута для поиска.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает S_OK, если пользовательский атрибут определен на этом поле, в противном случае возвращается S_FALSE.

## <a name="remarks"></a>Примечания
 Чтобы получить байты атрибутов, связанные с пользовательским атрибутом, позвоните в метод [GetCustomAttributeByName.](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)

## <a name="see-also"></a>См. также
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
