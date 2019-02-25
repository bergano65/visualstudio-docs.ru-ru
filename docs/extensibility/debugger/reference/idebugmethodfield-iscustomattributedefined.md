---
title: IDebugMethodField::IsCustomAttributeDefined | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08534abc468ac358d7c5eeba25129d9752f84e5a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717095"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Определяет, было ли определено определенного настраиваемого атрибута.

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

#### <a name="parameters"></a>Параметры
 `pszCustomAttributeName`

 [in] Строка, содержащая имя настраиваемого атрибута для поиска.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение S_OK, если настраиваемого атрибута определен в этом методе, в противном случае возвращает значение S_FALSE.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)