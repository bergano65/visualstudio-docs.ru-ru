---
title: Метод IJsEnumDebugProperty::Next | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728824"
---
# <a name="ijsenumdebugpropertynext-method"></a>Метод IJsEnumDebugProperty::Next
Считывает свойства для этого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [out] Объект, представляющий свойства браузера.  
  
 `pActualCount`  
 [out] Фактическое число свойств объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)