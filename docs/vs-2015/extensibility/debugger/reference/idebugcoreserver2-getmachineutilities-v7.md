---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843224"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает служебные программы компьютера для сервера.  
  
> [!NOTE]
> Этот метод является устаревшим: не используйте ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] всегда возвращает `E_NOTIMPL` , если вызывается этот метод). Он хранится по историческим причинам.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUtil`  
 заполняет Возвращает `IDebugMDMUtil2_V7` интерфейс, представляющий сведения о служебных программах компьютера.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL` , указывающее, что метод не реализован.  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] всегда возвращает `E_NOTIMPL` , если вызывается этот метод.  
  
## <a name="see-also"></a>См. также:  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
