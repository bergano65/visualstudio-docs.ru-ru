---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67da86fd82020ef811484cb91dcd46f5f2b850da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942783"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Определяет, существует ли настраиваемый атрибут по имени.  
  
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
 Возвращает значение S_OK, если настраиваемого атрибута определен на это поле, в противном случае возвращает значение S_FALSE.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить атрибут байт, связанных с помощью настраиваемого атрибута, вызовите [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)