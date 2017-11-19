---
title: "IDebugMethodField::IsCustomAttributeDefined | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords: IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bf6d2dbc915638005f377826c5504b2f6bdf859
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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