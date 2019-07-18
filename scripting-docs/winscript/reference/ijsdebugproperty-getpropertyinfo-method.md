---
title: Метод IJsDebugProperty::GetPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0769bf137845655c3fe0bf87bf0a57c6c6cbc09e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977775"
---
# <a name="ijsdebugpropertygetpropertyinfo-method"></a>Метод IJsDebugProperty::GetPropertyInfo
Получает сведения для этого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `nRadix`  
 [in] Основание системы счисления для использования.  
  
 `pPropertyInfo`  
 [out] Сведения об объекте.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)