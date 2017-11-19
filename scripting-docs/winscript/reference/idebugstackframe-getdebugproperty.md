---
title: "IDebugStackFrame::GetDebugProperty | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetDebugProperty
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 898c80dc4f5ef9010db6396a78c1b17b50603dc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
Возвращает обозреватель свойств для текущего кадра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDebugProp`  
 [out] Обозреватель свойств для текущего кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает обозреватель свойств для текущего кадра.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)