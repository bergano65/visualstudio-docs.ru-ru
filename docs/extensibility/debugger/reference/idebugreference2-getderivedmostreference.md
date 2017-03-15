---
title: "IDebugReference2::GetDerivedMostReference | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 10
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
ms.openlocfilehash: 1cb281e93eb462de607f83a4e1d2d72785cef9a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Возвращает ссылку на производного ссылки. Зарезервировано для будущего использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDerivedMost`  
 [out] Возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий свойство производного.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
 Например, если это свойство описывает объект, реализующий интерфейс `ClassRoot` , но это на самом деле экземпляр `ClassDerived` , производный от `ClassRoot`, этот метод возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий ссылку на `ClassDerived` объект.  
  
## <a name="see-also"></a>См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
