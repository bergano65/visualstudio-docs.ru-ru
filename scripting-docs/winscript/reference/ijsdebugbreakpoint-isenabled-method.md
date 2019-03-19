---
title: Метод IJsDebugBreakPoint::IsEnabled | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99df17f73896b4dd04481315b04e1672a56285a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159508"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>Метод IJsDebugBreakPoint::IsEnabled
Определяет, включена ли точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pIsEnabled`  
 [out] Возвращает значение true, если точка останова включена; в противном случае возвращает false.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает E_UNEXPECTED, если вызван на удаленной точке останова.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)