---
title: Метод IJsEnumDebugProperty::Next | Документация Майкрософт
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
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086779"
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