---
title: Метод IJsDebugBreakPoint::Disable | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24584d0e9708dab4879ceb26f0af5e142936210a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583247"
---
# <a name="ijsdebugbreakpointdisable-method"></a>Метод IJsDebugBreakPoint::Disable
Отключает точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает E_UNEXPECTED, если вызван на удаленной точке останова. Возвращает значение S_FALSE, если вызван на уже отключенной точки останова.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)