---
title: 'Метод метод ijsdebugdatatarget:: Реадбстр | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b125f58b4be279eac167b803ed6a683c1fb04ddf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572441"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>Метод IJsDebugDataTarget::ReadBSTR
Считывает строку BSTR из целевого объекта отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 окне Адрес, из которого производится чтение.  
  
 `pString`  
 заполняет Значение BSTR, считанное из целевого объекта отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает E_JsDEBUG_INVALID_MEMORY_ADDRESS, если адрес является недопустимым.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)