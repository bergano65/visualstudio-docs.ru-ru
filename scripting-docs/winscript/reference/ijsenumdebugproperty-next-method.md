---
title: Метод IJsEnumDebugProperty::Next | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ec6a1dded8c24de06a5746261a19b6609a97ada
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977543"
---
# <a name="ijsenumdebugpropertynext-method"></a>Метод IJsEnumDebugProperty::Next
Считывает свойства для данного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `count`  
 [in] Число свойств для чтения.  
  
 `ppDebugProperty`  
 [out] Объект, представляющий обозреватель свойств.  
  
 `pActualCount`  
 [out] Фактическое число свойств объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)