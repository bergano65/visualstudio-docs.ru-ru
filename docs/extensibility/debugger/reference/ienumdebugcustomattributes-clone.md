---
title: "IEnumDebugCustomAttributes::Clone | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
caps.latest.revision: 8
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
ms.openlocfilehash: 97fe72954a3d1d178f17f5b3a582ee7d7ae4aa55
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Создает перечислитель с тем же состоянием, что и текущий перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IEnumCustomAttributes** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppEnum  
 [out] Возвращает копию этого перечисления как отдельный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Копия перечисления имеет том же состоянии, что и исходный в момент вызова этого метода. Тем не менее копирования и исходного состояния отделены и могут изменяться по отдельности.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
