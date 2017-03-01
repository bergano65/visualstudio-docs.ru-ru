---
title: "IDebugObject::IsNullReference | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8dc2376af276a99dd63bbc4d4ffd89825acc1762
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Проверяет, является ли этот объект является пустой ссылкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```c#  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsNull`  
 [out] Возвращает ненулевое значение (`TRUE`) Если этот объект является пустой ссылкой; в противном случае — возвращает ноль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Указатель null означает пустой объект или объект, который не назначен.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
