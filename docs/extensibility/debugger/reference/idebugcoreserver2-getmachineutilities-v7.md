---
title: "IDebugCoreServer2::GetMachineUtilities_V7 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
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
ms.openlocfilehash: 8cec5befece6b3415a903ed84d8d31cbe3988ee8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Этот метод возвращает машины служебные программы для сервера.  
  
> [!NOTE]
>  Этот метод устарел: не используйте ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода). Он сохраняется по историческим причинам.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```c#  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUtil`  
 [out] Возвращает `IDebugMDMUtil2_V7` интерфейс, представляющий сведения о служебных программ машине.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает `E_NOTIMPL`, указывающее, что метод не реализован.  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]всегда возвращает `E_NOTIMPL` при вызове этого метода.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
