---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da6b9c27667ca0960b43ba6e14f0fd4b1fab2634
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Параметры  
 `pszCustomAttributeName`  
 [in] Строка, содержащая имя настраиваемого атрибута для поиска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение S_OK, если настраиваемого атрибута определен для данного поля в противном случае возвращает значение S_FALSE.  
  
## <a name="remarks"></a>Примечания  
 Для получения байтов атрибут, связанный с настраиваемого атрибута, вызовите [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)