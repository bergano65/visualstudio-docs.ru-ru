---
title: BP_LOCATION_RESOLUTION | Документация Майкрософт
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
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c18a424040ebc305efa57bf61feceed54b6e2e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720870"
---
# <a name="bplocationresolution"></a>BP_LOCATION_RESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает разрешение точку останова в определенном месте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## <a name="members"></a>Участники  
 pResolution  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) объект, который определяет тип точки останова и сведения о разрешении.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

