---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad2a147aff291feb776d7b61f4e836651ed642fd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301110"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает машины служебные программы для сервера.  
  
> [!NOTE]
>  Этот метод является устаревшим: не используйте ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода). Он сохраняется по историческим причинам.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUtil`  
 [out] Возвращает `IDebugMDMUtil2_V7` интерфейс, который представляет сведения о машине служебные программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает `E_NOTIMPL`, указывающее, что метод не реализован.  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

