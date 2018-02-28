---
title: "IEnumDebugExtendedPropertyInfo::Skip | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7f686ccaa5a3195b82458cf3ee11f02be104f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Пропускает указанное число `ExtendedDebugPropertyInfo` структуры в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество `ExtendedDebugPropertyInfo` структуры в последовательность перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимую `HRESULT`, обычно `S_OK`. Возвращает `S_FALSE` и устанавливает текущий указатель элемента в конец перечисления, если `celt` больше, чем число элементов влево в перечислителе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)