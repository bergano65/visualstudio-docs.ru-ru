---
title: 'Метод метод ijsdebugproperty:: Members | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3e700e51dea6723238437bf1fed741698097ae2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574051"
---
# <a name="ijsdebugpropertygetmembers-method"></a>Метод IJsDebugProperty::GetMembers
Возвращает элементы этого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `members`  
 окне Флаги для указания элементов, включенных в сведения об элементе.  
  
 `ppEnum`  
 заполняет Элементы объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)