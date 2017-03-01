---
title: "IDebugObject2::CreateAlias | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
caps.latest.revision: 7
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
ms.openlocfilehash: f001d55d1cfef8f900e783abba639f11aa7b41e5
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Создает уникальный идентификатор или псевдоним для этого объекта или возвращает существующего псевдонима.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int CreateAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppAlias`  
 [out] Псевдоним новую (или существующую).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Псевдоним является меткой, которая представляет определенный объект, пока объект находится в памяти.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
