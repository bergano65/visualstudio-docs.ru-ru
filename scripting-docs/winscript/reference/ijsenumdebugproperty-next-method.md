---
title: 'Метод метод ijsenumdebugproperty:: Next | Документация Майкрософт'
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
ms.openlocfilehash: 48c4506d783093395b2d88b7a71d56e3a89d24e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573988"
---
# <a name="ijsenumdebugpropertynext-method"></a>Метод IJsEnumDebugProperty::Next
Считывает свойства для этого объекта.  
  
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
 окне Число свойств для чтения.  
  
 `ppDebugProperty`  
 заполняет Объект, представляющий обозреватель свойств.  
  
 `pActualCount`  
 заполняет Фактическое число свойств объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)