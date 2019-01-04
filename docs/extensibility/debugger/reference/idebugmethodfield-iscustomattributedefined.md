---
title: IDebugMethodField::IsCustomAttributeDefined | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: faf06a9a6a15b751116b3d1e64b28459f56c27db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903247"
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
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)